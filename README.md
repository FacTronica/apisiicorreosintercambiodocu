# API Consulta Correo de Intercambio SII por RUT

## Descripción

Esta API permite consultar el **correo electrónico de intercambio actualizado** de un contribuyente a partir de su **RUT**.

El objetivo principal es facilitar la integración de sistemas ERP, facturación electrónica, recepción de DTE y procesos automáticos relacionados con documentos tributarios electrónicos en Chile.

---

## Endpoint

```http
GET https://dev.factronica.cl/api/sii_herramientas_correointercambio/index.php
```

---

## Parámetros

| Parámetro | Tipo | Obligatorio | Descripción |
|---|---|---|---|
| `rut` | string | Sí | RUT del contribuyente con guion y dígito verificador. |

### Ejemplo

```http
https://dev.factronica.cl/api/sii_herramientas_correointercambio/index.php?rut=77777777-7
```

---

## Autenticación

La API requiere enviar un token de acceso en la cabecera HTTP:

```http
X-API-KEY: TU_TOKEN_API
```

---

## Ejemplo en PHP 

```php
<?php
#
# ============================================
# TEST API CONSULTA CONTRIBUYENTE
# Compatible PHP 
# ============================================

#
# URL API
$url = "https://dev.factronica.cl/api/sii_herramientas_correointercambio/index.php?rut=77777777-7";

#
# TOKEN API
$token = "TU_TOKEN_API";

#
# INICIAR CURL
$curl = curl_init();

#
# CONFIGURAR CURL
curl_setopt_array($curl, array(
    CURLOPT_URL => $url,
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_TIMEOUT => 30,
    CURLOPT_HTTPGET => true,
    CURLOPT_HTTPHEADER => array(
        "X-API-KEY: " . $token
    )
));

#
# EJECUTAR
$respuesta = curl_exec($curl);

#
# ERROR CURL
if (curl_errno($curl)) {

    echo "ERROR CURL: " . curl_error($curl);

} else {

    #
    # HTTP STATUS
    $httpcode = curl_getinfo($curl, CURLINFO_HTTP_CODE);

    echo "HTTP STATUS: " . $httpcode . "<hr>";

    #
    # MOSTRAR RESPUESTA RAW
    echo "<h3>RESPUESTA RAW</h3>";

    echo "<pre>";
    print_r($respuesta);
    echo "</pre>";

    #
    # CONVERTIR JSON A ARRAY
    $json = json_decode($respuesta, true);

    #
    # VALIDAR JSON
    if (!is_array($json)) {

        echo "ERROR DECODIFICANDO JSON";
        exit;
    }

    #
    # VALIDAR RESPUESTA
    if ($json["estado"] == true) {

        echo "<hr>";

        echo "RUT: " . $json["datos"]["rut"] . "<br>";
        echo "RAZON SOCIAL: " . $json["datos"]["razon_social"] . "<br>";
        echo "NUM RESOLUCION: " . $json["datos"]["num_resolucion"] . "<br>";
        echo "FECHA RESOLUCION: " . $json["datos"]["fecha_resolucion"] . "<br>";
        echo "EMAIL: " . $json["datos"]["email"] . "<br>";
        echo "URL: " . $json["datos"]["url"] . "<br>";

    } else {

        echo "<hr>";
        echo "ERROR API: " . $json["mensaje"];
    }
}

#
# CERRAR CURL
curl_close($curl);
```

---

## Ejemplo de respuesta correcta

```json
{
    "estado": true,
    "mensaje": "Consulta realizada correctamente",
    "datos": {
        "rut": "77777777-7",
        "razon_social": "EMPRESA DEMO SPA",
        "num_resolucion": "123",
        "fecha_resolucion": "2024-01-01",
        "email": "intercambio@empresa.cl",
        "url": "https://..."
    }
}
```

---

## Campos de respuesta

| Campo | Tipo | Descripción |
|---|---|---|
| `estado` | boolean | Indica si la consulta fue exitosa. |
| `mensaje` | string | Mensaje descriptivo de la respuesta. |
| `datos.rut` | string | RUT consultado. |
| `datos.razon_social` | string | Razón social del contribuyente. |
| `datos.num_resolucion` | string | Número de resolución asociada. |
| `datos.fecha_resolucion` | string | Fecha de resolución. |
| `datos.email` | string | Correo electrónico de intercambio actualizado. |
| `datos.url` | string | URL relacionada al registro consultado, si existe. |

---

## Ejemplo de respuesta con error

```json
{
    "estado": false,
    "mensaje": "RUT no encontrado"
}
```

---

## Códigos HTTP recomendados

| Código | Descripción |
|---|---|
| `200` | Consulta procesada correctamente. |
| `400` | Parámetro `rut` no enviado o formato inválido. |
| `401` | Token API no enviado o inválido. |
| `404` | RUT no encontrado. |
| `500` | Error interno del servidor. |

---

## Validaciones recomendadas en el cliente

Antes de consumir la API se recomienda validar:

1. Que el RUT no esté vacío.
2. Que el RUT incluya guion y dígito verificador.
3. Que se envíe la cabecera `X-API-KEY`.
4. Que la respuesta sea un JSON válido.
5. Que el campo `estado` sea `true` antes de leer el arreglo `datos`.

---

## Ejemplo de consumo con cURL

```bash
curl -X GET "https://dev.factronica.cl/api/sii_herramientas_correointercambio/index.php?rut=77777777-7" -H "X-API-KEY: TU_TOKEN_API"
```
---

## Uso esperado

Esta API puede ser utilizada en sistemas ERP, sistemas de facturación electrónica, módulos de recepción de DTE o procesos automáticos que necesiten obtener o actualizar el correo de intercambio de un contribuyente.

---

## Autor

**Factronica ERP**  
API para consulta de correo de intercambio de contribuyentes.
