# Errores

Los código de errores en los status http de nuestras APIs son los siguientes:


| Error Code | Meaning                                                                                                    |
|------------|------------------------------------------------------------------------------------------------------------|
| 400        | Bad Request -- La petición efectuada no es válida, revise los parámetros.                                  |
| 401        | Unauthorized -- El API KEY utilizado no es válido o su cuenta no está activa.                              |
| 403        | Forbidden -- Usted no tiene acceso a este recurso.                                                         |
| 404        | Not Found -- El recurso que está intentando acceder no exsite.                                             |
| 405        | Method Not Allowed -- El método http que está utilizando no es el apropiado para el recurso.               |
| 406        | Not Acceptable -- El formato que está usando para acceder al recurso no es un json valido.                 |
| 410        | Gone -- El recurso que está intentado acceder ha sido removido de nuestro servidores.                      |                                                                               |
| 429        | Too Many Requests -- Ha excedido la cuota de peticiones mensuales o concurrentes                           |
| 500        | Internal Server Error -- Ha ocurrido un error interno en nuestros servidores y estamos trabajando en ello. |
| 503        | Service Unavailable -- El servicio está temporalmente fuera de servicio debido a mantenimientos.           |
