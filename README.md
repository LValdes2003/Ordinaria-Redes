# Ordinaria-Redes

### Pregunta 1
- Describe brevemente las principales diferencias entre el modelo OSI y el modelo TCP/IP (número de capas, orientación y tratamiento de la capa de aplicación).

|OSI | TCP/IP |
|-|-|
|7 capas |4 capas |
|Centrado en conexiones (TCP) |No centrado en conexiones (TCP o UDP) |
|Modelo no práctico |Modelo práctico |
|Ruteo de paquetes en capa Red |Ruteo de paquetes en capa Internet |
|Se pueden definir protocolos en cada capa |Protocolos estandarizados |

- Explica el rol de la capa de transporte en la comunicación de redes y compara los protocolos TCP y UDP en términos de:
  - Orientación a conexión
  - Fiabilidad y control de errores
  - Velocidad y aplicaciones típicas
 
La capa de transporte se encarga de transmisión de datos entre aplicaciones.

|TCP | UDP |
|-|-|
|Orientado a conexiones |No orientado a conexiones |
|Control de errores (Cada paquete necesita confirmación del recipiente) |Ningún control de errores (A veces checksum) |
|Mas lento |Mas rápido |
|Para situaciones donde no puede haber datos incorrectos (texto, archivos) |Para cuando hay que transmtir datos rápidamente (streaming) |

### Pregunta 2
- Describe el proceso completo de resolución de nombres en el Sistema de Nombres de Dominio (DNS), desde que un usuario ingresa una URL hasta que se establece la conexión con el servidor web.
El usuario ingresa la URL, el rúter busca en su tabla si corresponde a una dirección IP. Si no, hace un request a su correspondiente servidor DNS. Si todavía no se encuentra, se busca por el domain (.com, .net, .es) y el servidor correspondiente manda la dirección IP. Esto se hace usando UDP para que sea un proceso mas rápido.

- Compara el funcionamiento de HTTP y FTP, haciendo hincapié en:
  - El método de conexión (un único canal vs. dos conexiones para control y datos)
  - Las principales aplicaciones de cada uno
