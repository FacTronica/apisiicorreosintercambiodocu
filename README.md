# API Consulta Correo de Intercambio SII para Facturacion Electronica

> **Api para obtener en tiempo real el correo de intercambio de sus clientes antes de emitir un DTE.**  
> Evite rechazos, reclamos por documentos no recibidos, retrasos de pago y reprocesos operativos en su ERP o plataforma de facturacion.

<p>
  <strong>Actualizacion diaria</strong> &nbsp;|&nbsp;
  <strong>API REST JSON</strong> &nbsp;|&nbsp;
  <strong>Datos sincronizados desde SII</strong> &nbsp;|&nbsp;
  <strong>Compatible con ERP, ecommerce e integradores</strong>
</p>

Más info en: https://sistemafactronica.cl/api_sii_correosintercambio.php
---

## Que es el correo de intercambio

El **correo de intercambio** es la casilla electronica registrada por un contribuyente para recibir los archivos **XML de Documentos Tributarios Electronicos (DTE)** enviados por sus proveedores.

Esta casilla se utiliza en operaciones como:

- Facturas electronicas.
- Notas de credito y debito.
- Guias de despacho.
- Otros documentos tributarios electronicos.

> El correo de intercambio **no es un correo comun de contacto comercial**. Es una pieza critica del flujo tributario electronico entre empresas, sistemas ERP, plataformas de facturacion e integradores DTE.

---

## Por que es critico validar este correo

Cuando una empresa emite un DTE, no basta con generar la factura. El XML debe llegar correctamente al receptor para que el documento pueda ser procesado por su sistema contable, ERP o flujo de compras.

### Flujo correcto

```text
Proveedor
  -> XML enviado
  -> Correo de intercambio vigente
  -> ERP receptor
  -> Registro de compras
  -> Aprobacion y pago
```

### Flujo con correo incorrecto o desactualizado

```text
Proveedor
  -> XML no recibido
  -> Cliente no visualiza el DTE
  -> Factura queda fuera del flujo interno
  -> Reclamos y reenvios manuales
  -> Retrasos de pago o rechazo operativo
```

---

## Problemas reales de usar un correo desactualizado

Un correo de intercambio incorrecto puede generar impactos operativos inmediatos:

| Problema | Impacto |
| --- | --- |
| Facturas no visibles en el ERP del cliente | El documento no entra al flujo de aprobacion |
| Reclamos por "factura no recibida" | Aumenta la carga de soporte y cobranza |
| Reenvio manual de XML | Se pierde automatizacion y trazabilidad |
| Demoras en conciliacion contable | Compras y finanzas trabajan con informacion incompleta |
| Retrasos en pago a proveedores | El DTE no avanza en el proceso interno |
| Riesgo de incumplimiento operativo | Se dificulta acreditar recepcion documental |

---

## PDF vs XML: una diferencia clave

> **El PDF no reemplaza al XML.**

El **PDF** es solo una representacion visual de la factura. Sirve para lectura humana, pero no es el documento usado por los sistemas para integracion tributaria y recepcion automatica.

El **XML del DTE** es el archivo electronico que permite a los sistemas validar, registrar, integrar y procesar la informacion tributaria entre empresas.

| Archivo | Funcion |
| --- | --- |
| PDF | Visualizacion del documento para personas |
| XML | Documento electronico usado para integracion entre sistemas |

---

## Beneficios de consultar el correo en tiempo real

| Metodo | Riesgo operativo | Recomendacion |
| --- | ---: | --- |
| Correo guardado hace meses | Alto | No recomendado |
| Excel o maestro manual | Alto | Propenso a errores |
| Consulta API actualizada diariamente | Bajo | Recomendado |

Con la API de Factronica puede validar el correo de intercambio antes de emitir, reenviar o sincronizar documentos, manteniendo su operacion conectada con informacion actualizada.

---

## Por que cambia el correo de intercambio

Las empresas pueden modificar su casilla por razones tecnicas u operativas:

- Cambio de proveedor de facturacion electronica.
- Migracion de ERP.
- Cambio de integrador DTE.
- Centralizacion de recepcion documental.
- Actualizacion de datos registrados ante el SII.

Por eso, **no es recomendable guardar el correo indefinidamente** sin volver a validarlo.

---

## Actualizacion diaria desde fuentes oficiales

Factronica sincroniza diariamente la informacion publicada por el SII para mantener disponible una base actualizada de correos de intercambio.

Esto permite entregar una respuesta confiable para sistemas que necesitan automatizacion, trazabilidad y continuidad operacional.

**Indicadores de servicio**

| Caracteristica | Detalle |
| --- | --- |
| Base procesada | +1.000.000 correos |
| Actualizacion | Diaria y automatica |
| Formato | REST JSON |
| Integracion | Compatible con cualquier ERP |
| Respuesta | En milisegundos |

---

## Casos de uso

### ERP y software de facturacion

Valide automaticamente el correo de intercambio antes de emitir un DTE, reduciendo rechazos y reclamos por documentos no recibidos.

### Marketplace y ecommerce

Automatice el envio de XML a clientes, proveedores y empresas que requieren recepcion documental integrada.

### Integradores contables

Sincronice la recepcion documental y mejore la trazabilidad de facturas, notas de credito, guias y otros DTE.

### Sistemas de compras

Detecte cambios de casilla de intercambio y evite que documentos tributarios queden fuera del flujo de aprobacion.

### Automatizacion tributaria

Reduzca errores operativos, reenvios manuales y validaciones internas repetitivas.

---

## Ejemplo tecnico

### Request

```http
GET /api/correo-intercambio?rut=76086428-5
```

### Response

```json
{
  "estado": true,
  "rut": "76086428-5",
  "razon_social": "EMPRESA DEMO SPA",
  "correo_intercambio": "dte@empresa.cl",
  "actualizado": "2026-05-21"
}
```

---

## Arquitectura recomendada

```text
ERP / Ecommerce / Plataforma DTE
  -> Factronica API
  -> Base sincronizada SII
  -> Correo de intercambio actualizado
  -> Envio XML al receptor correcto
```

### Linea de actualizacion

```text
SII publica informacion
  -> Factronica sincroniza diariamente
  -> API normaliza datos
  -> Cliente consulta por RUT
  -> Sistema emite o reenvia con mayor confianza
```

---

## Para proveedores de software

Esta API esta pensada para empresas que necesitan integrar validacion tributaria en sus propios productos:

- ERP.
- Software contable.
- Ecommerce B2B.
- Middleware DTE.
- Integradores tributarios.
- Plataformas SaaS.
- Sistemas de compras y abastecimiento.

> Si su plataforma emite, recibe o procesa DTE, validar el correo de intercambio antes de operar mejora la continuidad del flujo documental.

---

## Funcionalidades premium sugeridas

Estas capacidades pueden complementar la consulta individual:

| Funcionalidad | Valor para el cliente |
| --- | --- |
| Consulta batch por multiples RUT | Procesar carteras completas de clientes o proveedores |
| Webhooks de cambios | Avisar cuando cambia un correo de intercambio |
| Historial de cambios | Auditar modificaciones de casillas |
| Validacion MX/DNS | Verificar estado tecnico del dominio de correo |
| Descarga diaria CSV | Mantener sistemas internos sincronizados |
| SDK PHP / Node / Python | Acelerar implementaciones tecnicas |

---

## Preguntas frecuentes

### El correo viene directamente del SII?

Si. La informacion es obtenida desde bases oficiales publicadas por el SII y sincronizada por Factronica.

### Cada empresa tiene un correo distinto?

Si. Cada contribuyente puede registrar su propia casilla de intercambio para recepcion de DTE.

### Que pasa si envio el XML al correo incorrecto?

El receptor podria no recibir el DTE en su sistema ERP, generando reclamos, reenvios manuales y demoras de pago.

### El PDF reemplaza al XML?

No. El PDF es una representacion visual. El XML es el documento electronico usado para integracion tributaria entre sistemas.

### Con que frecuencia se actualiza la informacion?

Factronica sincroniza diariamente la informacion publicada por el SII.

---

## Terminos relacionados

Correo intercambio SII, mail intercambio DTE, consultar correo facturacion electronica, API SII Chile, XML factura electronica Chile, correo recepcion DTE, integracion facturacion electronica, recepcion automatica XML, consulta contribuyente SII, API RUT Chile.

---

## El correo de Intercambio es Muy Importante

> **Evite rechazos y retrasos de pago validando el correo de intercambio antes de emitir cada DTE.**

Mantenga su ERP sincronizado con los correos oficiales de intercambio publicados por el SII y reduzca errores operativos en la recepcion documental electronica.

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
