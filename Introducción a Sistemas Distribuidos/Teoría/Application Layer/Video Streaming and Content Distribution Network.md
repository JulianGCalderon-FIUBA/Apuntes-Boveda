## 1. Internet Video

En las aplicaciones de *streaming,* el medio son videos pre-grabados, almacenados en servidores. Los usuarios pueden enviar peticiones a los servidores para ver estos videos bajo demanda.

Un video es una secuencia de imágenes, sin compresión, puede ser considerado como un arreglo de píxeles, cada uno codifica su color y luminosidad. Estos videos pueden ser comprimidos, intercambiando calidad por *bit rate.*

## 2. HTTP Streaming and DASH

En el *streaming* con HTTP, el video simplemente es almacenado en un servidor HTTP como un archivo ordinario. El cliente establece una conexión IP y hace un pedido por el mismo. Desde el lado del cliente, este se guarda en el buffer de la aplicación y se reproduce a medida que se descarga.

Con el tiempo, surgió un nuevo tipo de *streaming*. El *Dynamic Adaptive Streaming over HTTP (DASH)*: esta técnica provee la posibilidad de pedir un video en distintos *bit rates,* según la calidad de la conexión. El cliente hace un pedido por un pequeño segmento del video, los segmentos se piden uno a la vez a través de HTTP.

En DASH, cada versión del video está almacenada en una URL diferente. Además, el servidor posee un *manifest file* que muestra las distintas URL para cada versión, así como su *bitrate*.

## 3. Content Distribution Networks

La mayoría de grandes compañías de *streaming* utilizan **Content Distribution Networks (CDN)**. Estas redes gestionan servidores geográficamente distribuidos y guardan copias de los videos. Estas redes también tratan de redirigir a cada cliente a una localización que provea la mejor experiencia de usuario.

Usualmente, estas redes adoptan una de dos filosofías:

- **Enter Deep:** Una filosofía consiste en entrar completamente en las redes de acceso de los ISP, el objetivo es acercarse a los *end users*.
- **Bring Home:** Esta segunda filosofía consiste en construir grandes agrupamientos en un pequeño número de lugares. Esto resulta en menos mantenimiento, pero un mayor *delay*.

Usualmente, si un CDN no tiene un video, este hace un pedido de una copia y a medida que la descarga, se la envía al cliente.

## CDN Operation

La mayoría de los CDN utilizan el sistema DNS para redirigir pedidos. Cuando se trata de acceder un pedido, primero se le envía la *request* al *authoritative DNS server.* Este, redirige el pedido al *authoritative server* del *content provider*. Este devuelve la dirección IP de algún servidor que considere adecuado. Finalmente, el cliente pide el video a través de esta IP.

## Cluster Selection Strategies

El CDN obtiene la dirección IP del cliente a través del *DNS look-up*. Con esta información, el servidor puede determinar el clúster.

Una estrategia simple es la de seleccionar el clúster que esté geográficamente más cerca. Pero esto no siempre resultará en el mejor rendimiento. Esto se debe a que muchas veces este no coincide con el más cercano en número de saltos.

Para determinar el mejor clúster, las CDN realizan medidas en tiempo real del *delay* y la pérdida de información entre los clientes y los clústeres.
