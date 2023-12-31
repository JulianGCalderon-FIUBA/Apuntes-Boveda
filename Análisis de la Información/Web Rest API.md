Para armar modelos de vista, el **frontend** interactúa con la API. Luego devuelve estos modelos para que el navegador lo renderice. Estos pedidos se realizan a través de un request HTTP. La respuesta suele estar en formato JSON, el cual es utilizado para armar las vistas.

Para el **backend**, se suele utilizar Java con Spring Boot, este es un *framework* de Java utilizada para múltiples cosas, entre ellas aplicaciones web. Para la base de datos, existen distintos motores (MySQL)

Para el *frontend*, utilizaremos principalmente React, el cual se puede ejecutar tanto en la nube como en la web. (Azure, Google Cloud, GitHub).

Nuestro código estará almacenado en un repositorio en la nube, GitHub, GitLab, Bitbucket. Para verificar que nuestros cambios cumplan lo esperado, hay distintos servidores para automatización e integración continua.

## Backend

Tendremos un modelo de capas, la primera es la capa de API, la cual recibe peticiones. Luego se ejecuta cierta lógica de negocio determinada (capa de servicio), sé a la base de datos a través de capa de persistencia y acceso de datos. Finalmente devuelve una respuesta.

## REST

Es un tipo de API, que cumple con ciertos requisitos. Se puede implementar de muchas formas, una de ellas es utilizando HTTP.

- **POST:** no idempotente, no es seguro (crea recursos)
- **GET:** idempotente, seguro (lee recursos)
- **PUT:** idempotente, no es seguro (actualiza recursos)
- **DELETE:** idempotente, no es seguro (borra recursos)

Las siglas CRUD se suelen usar normalmente en el lenguaje de negocio: las altas, bajas, modificaciones y consultas.

Un pedido idempotente es aquel que si se ejecuta dos veces, el cambio ocurre dos veces. Ej.: Con cada pedido de post, se crea un recurso.

Hay distintos elementos en los mensajes de la API:

- **Path params:** Comúnmente utilizado para identificar recursos. Ej.: `/accounts/{accountId}`. No puede utilizar verbos.
- **Query params:** Comúnmente utilizado para filtrar y ordenar. Le sigue a la URL y comienza con un '?'. Ej.: `/cars?color=blue`
- **Body:** Se utiliza para enviar o recibir un recurso determinado. Usualmente, es un JSON.
