---
title: Manual de Usuario

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Portal del desarrollador</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentación de las APIs de duqto.
---

# Getting Started

## Registro

Entrar al [Portal del Desarrollador](https://d32sbd4rsmbmrc.cloudfront.net/) y en la parte superior izquierda hacer click en 'Registro'.

Una vez abierto el formulario, llenar los datos que se solicitan. Es muy importante que el correo que se coloque sea válido porque se enviará un correo de verificación.

Posteriormente se mostrará la opcion de introducir el código de confirmación enviado por correo y con esto el usuario quedaría registrador y aprobado.

## Login al portal del desarrollador

Una vez registrado, ya podrás hacer uso del portal del desarrollador y acceder a las APIs.

Entrar al [Portal del Desarrollador](https://d32sbd4rsmbmrc.cloudfront.net/) y en la parte superior izquierda hacer click en 'Autenticar'.

Introducir los datos del formulario que se solicitan y ya quedará autenticado.

## Suscribirse a un API

Una vez autenticado en el portal, en la barra de navegación en la parte superior izquierda aparecerá una opción llamada 'Mis APIs'.

Al seleccionarla se podrán listar todas las APIs disponibles de duqto en el menú a la izquierda. 

Cuando se selecciona una de estas, en la parte central se mostrará en swagger y el botón de suscribirse.

Es importante entender que aunque se puedan visualizar las APIs si el usuario no se suscribe a las mismas no podrá posteriormente acceder a ellas.

## Mi espacio

Una vez autenticado en el portal, aparecerá en la parte superior derecha una opción llamada 'Mi espacio' en ella se podrán visualizar 3 cosas importantes:
1. El API KEY del usuario.
2. Las restricciones de uso de las APIs (si es que está suscrito a alguna)
3. El histórico de request a las APIs (si es que está suscrito a alguna)


# Autenticación

> La autorización está basada en el API KEY:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "X-API-KEY: your-api-key"
```

> Asegúrate de remplazar `your-api-key` con tu API KEY obtenido en la sección 'Mi Espacio'.

duqto usa API KEYs para permitir peticiones. Puedes registrarte y suscribirte en nuestro [Portal de Desarrolladores](https://d32sbd4rsmbmrc.cloudfront.net/).

duqto espera que el API KEY esté incluido en todas las peticiones a los servicios en un header de la siguiente forma:

`X-API-KEY: your-api-key`

<aside class="notice">
Debes remplazar <code>your-api-key</code> con tu api key personal obtenido en la sección 'Mi Espacio' del portal del desarrollador.
</aside>

# Vector de Precios

## Obtener Vector de Precios de Renta Fija

```shell
curl -X GET "https://p2rtlb0c1e.execute-api.us-east-1.amazonaws.com/dev/vector-precios/renta-fija/{bolsa}/{fecha}" \
-H "accept: application/json" 
-H "x-api-key: your-api-key"
```

> El comando anterior devuelve un json parecido a este:

```json
{
  "statusCode": 200,
  "nextMarker": "VlAjQlZRIzIwMjItMDMtMjV8NTcxMDEwMTAwMDAxMjQwMTI4",
  "data": [
    {
      "creationDate": "2022-03-25T04:01:27.311Z",
      "titleCode": "005020300001250115",
      "qualification": "AAA",
      "issuer": "BCO. BOLIVARIANO",
      "title": "OCAS",
      "issuedDate": "15-Jan-20",
      "expirationDate": "15-Jan-25",
      "interestRate": "7.070%",
      "readjustmentForm": "TPR BCE + 1,5%",
      "referenceRate": "",
      "margin": "",
      "discountRate": "7.7687%",
      "equivalentPerformance": "7.6234%",
      "price": "98.4775%"
    },
    {
      "creationDate": "2022-03-25T04:01:27.311Z",
      "titleCode": "007010500001241220",
      "qualification": "AAA",
      "issuer": "BANCO PICHINCHA C.A.",
      "title": "OBL CLASE A",
      "issuedDate": "20-Dec-19",
      "expirationDate": "20-Dec-24",
      "interestRate": "5.870%",
      "readjustmentForm": "TASA LIBOR 12M+ SPREAD",
      "referenceRate": "",
      "margin": "",
      "discountRate": "5.8828%",
      "equivalentPerformance": "5.7573%",
      "price": "99.9814%"
    }
  ]
}
```

Este endpoint devuelve una página de con la información del vector de precios - rentas fijas por bolsa de valores y fecha.

### HTTP Request

`GET https://p2rtlb0c1e.execute-api.us-east-1.amazonaws.com/dev/vector-precios/renta-fija/{bolsa}/{fecha}?marker={marker}`

### Parámetros

| Parámetro | Tipo  | Obligatorio | Descripción                                                                                                              |
|-----------|-------|-------------|--------------------------------------------------------------------------------------------------------------------------|
| bolsa     | Path  | Sí          | Debe incluir el identificador de la bolsa de valores a la cual buscar, por ejemplo BVQ para la bolsa de valores de Quito |
| fecha     | Path  | Sí          | La fecha del vector de precios diario en formato YYYY-MM-DD, por ejemplo 2022-03-26.                                     |
| marker    | Query | No          | En el caso que se se esté paginando, se debe enviar este parámetro para obtener la próxima página.                       |


## Obtener vector de precios de renta variable

```shell
curl -X GET "https://p2rtlb0c1e.execute-api.us-east-1.amazonaws.com/dev/vector-precios/renta-variable/{bolsa}/{fecha}" \
-H "accept: application/json" \ 
-H "x-api-key: your-api-key"
```

> El comando anterior devuelve un json parecido a este:

```json
{
  "statusCode": 200,
  "data": [
    {
      "creationDate": "2022-03-26T04:00:19.280Z",
      "issuer": "ALICOSTA BK HOLDING",
      "bvqRuedas": "0",
      "bvqPresencia": "0.00%",
      "bvqPrecioCierre": "  *  ",
      "bvgRuedas": "0",
      "bvgPresencia": "0.00%",
      "bvgPrecioCierre": " * ",
      "precioCierreNacional": "  *  "
    },
    {
      "creationDate": "2022-03-26T04:00:19.280Z",
      "issuer": "BEVERAGE BRAND & PATENTS COMPANY BBPC S.A",
      "bvqRuedas": "1",
      "bvqPresencia": "1.61%",
      "bvqPrecioCierre": " 60.00 ",
      "bvgRuedas": "1",
      "bvgPresencia": "1.61%",
      "bvgPrecioCierre": " 59.00 ",
      "precioCierreNacional": " 59.00 "
    }
  ]
}
```

Este endpoint devuelve una página de con la información del vector de precios - rentas variable por bolsa de valores y fecha.

### HTTP Request

`GET https://p2rtlb0c1e.execute-api.us-east-1.amazonaws.com/dev/vector-precios/renta-variable/{bolsa}/{fecha}?marker={marker}`

### Parámetros

| Parámetro | Tipo  | Obligatorio | Descripción                                                                                                              |
|-----------|-------|-------------|--------------------------------------------------------------------------------------------------------------------------|
| bolsa     | Path  | Sí          | Debe incluir el identificador de la bolsa de valores a la cual buscar, por ejemplo BVQ para la bolsa de valores de Quito |
| fecha     | Path  | Sí          | La fecha del vector de precios diario en formato YYYY-MM-DD, por ejemplo 2022-03-26.                                     |
| marker    | Query | No          | En el caso que se se esté paginando, se debe enviar este parámetro para obtener la próxima página.                       |
