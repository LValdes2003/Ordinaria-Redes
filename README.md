https://github.com/LValdes2003/Ordinaria-Redes/
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
  
|HTTP | FTP |
|-|-|
|Solo usa un canal para datos |Dos canales para control y datos |
|Para transferir páginas web por el internet |Para transferir archivos |
|Mas rápido |Mas lento |

### Pregunta 3
- calcula la tasa de transmisión máxima para un canal con un ancho de banda de 400 MHz y una relación señal a ruido de 15 dB. (Recuerda que para convertir de dB a escala lineal.
1.993156857 GHz

- En un sistema en el que la primera portadora se sitúa a 1.2 GHz y cada canal ocupa 300 MHz, determina la frecuencia de la portadora inmediatamente anterior y la inmediatamente posterior. Explica la importancia de esta asignación para la eficiencia espectral.

- Explica brevemente el funcionamiento del Algoritmo de Dijkstra para encontrar la ruta más corta en un grafo ponderado y compáralo con el método de enrutamiento por inundación (Flooding), señalando ventajas y desventajas de cada enfoque.

El Algoritmo de Dijkstra usa vértices, con los nodos no visitados teniendo un valor infinito, y el nodo fuente teniendo un valor de 0. Luego va al nodo con distancia mínima, asignándolo como nodo actual. Sigue con este método, acumulando los valores de distancia, hasta llegar al nodo objetivo de manera óptima.  
El método por Inundación manda el paquete por todas las rutas disponibles, y escoge la más corta. Sus ventajas son que es un método simple y que siempre encuentra la ruta mas corta. La desventaja es que crea mucho tráfico en la red, y el volumen de paquetes puede crear errores.

### Pregunta 4
- Para la red 192.168.10.0/24, determina:
  - La dirección de broadcast.
  - El rango de direcciones válidas (primera y última dirección de host).

Broadcast: 192.168.10.255
Rango: 192.168.10.1-254

- Explica cómo se calcula el número de hosts disponibles en una subred y, aplicándolo a una red con máscara 255.255.255.192, indica cuántos equipos (hosts) se pueden conectar.

Primero, la máscara se convierte a binario: 11111111.11111111.11111111.11000000. Hay 6 0´s disponibles, así que hay 2^6-2 hosts disponibles (quitando dirección de red y broadcast). Hay 62 hosts disponibles.

### Pregunta 5
- Describe el proceso de establecimiento de conexión en TCP (Three-Way Handshake) y, a continuación, el proceso de terminación de conexión (Four-Way Handshake). Explica la importancia de cada fase.

Establecimiento  
El emisor manda un paquete al puerto TCP del receptor pidiendo una conexión TCP (Sin esto no pueden contactar). El receptor manda un paquete reconociendo el paquete del emisor para aceptar la solicitud (Así solo hay comunicación si los dos lados lo quieren). Finalmente, El emisor manda un paquete reconociendo el paquete del emisor (Cada paquete necesita ser reconocido para asegurar que no hay errores).

Terminación  
EL emisor que quiere terminar la correspondencia manda un paquete solicitándolo (Sin esto no se puede terminar). El receptor reconoce este paquete (Para evitar errores). El receptor también manda un paquete solicitando terminación (Así los dos están de acuerdo que quieren terminar). El emisor lo reconoce, y terminan la conexión (Otra vez evitando errores).

- Para un enlace con los siguientes parámetros:
  - RTT = 40 ms
  - Ancho de banda = 50 Mbps
  - MSS = 1,460 bytes
- Utilizando la relación calcula el tamaño óptimo de la ventana en bits y en bytes, y estima aproximadamente el número de segmentos MSS que pueden estar en tránsito simultáneamente.

0.04 s * 50.000.000 bps = 2.000.000 bits / 8 = 250.000 bytes
250.000 / 1.460 bytes por segmento ~= 171 segmentos

- Compara brevemente el cifrado simétrico y asimétrico (en cuanto al número de claves, velocidad y aplicaciones).
|Simétrico | Asimétrico |
|-|-|
|Receptor y emisor usan la misma clave |Receptor y emisor tienen sus propias claves (doble) |
|Mas rápido |Mas lento |
|Menos seguro |Mas seguro |
|Cifrar muchos datos (VPN, archivos) |Cifrar con mas seguridad (Criptomonedas, correo seguro) |

- Describe el funcionamiento básico del algoritmo RSA, incluyendo la generación de claves y el proceso de cifrado/descifrado. (Puedes ilustrar el proceso con un ejemplo numérico sencillo, por ejemplo usando...

El algoritmo RSA usa números primos grandes. Luego sacas el producto de los números, y encuentras otro número que no tiene factores comunes con (p - 1) x (q - 1). Finalmente calculas el número que, cuando se multiplica con este y se resta 1, es igual a (p - 1) x (q - 1). La clave pública es el producto original con el número sin factores comunes, y la privada es el producto con el último número.

p = 3. q = 11. n = p x q = 33. (p - 1)(q - 1) = 20.  
e no puede tener factores comunes con 20. e = 7.  
e x d - 1 = 20. d = 3.  
clave pública = (n, e). clave privada (n, d).

- Explica qué es un firewall y menciona dos tipos (por ejemplo, filtrado de paquetes y firewall de estado), indicando cómo contribuyen a la protección de la red.
Un firewall es un dispositivo que separa la red externa y la interna.
Un firewall puede filtrar paquetes, observando sus IPs de fuente y destino, el protocolo, y números de puerto para decidir si pueden pasar. De esta manera, ciertos protocolos pueden ser prevenidos mientras que otros pueden pasar sin problema.
Un firewall también puede observar los estados de redes conectadas. Una versión mas tradicional de firewall. Con esto, se pueden buscar anomalías y tomar acciones.

- Menciona brevemente la función de VPN e IPSec en el aseguramiento de la comunicación.
IPSec es un conjunto de protocolos para mantener seguridad en conexiones entre dispositivos que cifran paquetes y verifican sus fuentes. Estos protocolos hacen posibles los VPNs (Virtual Private Network). VPNs cifran la conexión entre dos redes, así que uno puede acceder a una red privada a través del internet. VPNs no necesitan usar IPSec, pero son los protocolos mas comunes en conjunto con VPN.
