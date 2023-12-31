En las bases de datos reales, múltiples usuarios realizan operaciones de consulta y/o actualización simultáneamente. Nos gustaría aprovechar la capacidad de procesamiento lo mejor posible al atender a los usuarios.

En un sistema monoprocesador, se puede utilizar multitasking. Varios hilos o procesos pueden estar corriendo concurrentemente.

En un sistema multiprocesador, se disponen de varias unidades de procesamiento que funcionan de forma simultánea. La base de datos se puede replicar, disponiendo de varias copias de algunas tablas (o fragmentos de tablas) en distintas unidades de procesamiento.

La concurrencia es la posibilidad de ejecutar múltiples transacciones en forma simultánea.

## Modelo de concurrencia

Utilizaremos el modelo de concurrencia solapada (*interleaved concurrency*), que considera las siguientes hipótesis:

1. Disponemos de un único procesador que puede ejecutar múltiples transacciones simultáneamente
2. Cada transacción está formada por una secuencia de instrucciones atómicas, que el procesador ejecuta de a una a la vez.
3. En cualquier momento, el *scheduler* puede suspender la ejecución de una transacción, e iniciar o retomar la ejecución de otra.

## Solapamiento

Un solapamiento entre dos [[Transacción|transacciones]] $T_1, T_2$ es una lista de $m(T_1) + m(T_2)$ instrucciones, en donde cada instrucción de $T_1$ y de $T_2$ aparece una única vez, y las instrucciones de cada transacción conservan el orden entre ellas dentro del solapamiento.

Podemos calcular la cantidad de solapamientos posibles como

$$
\frac{(m(T_1)+m(T_2))!}{m(T_1)!\cdot m(T_2)!}
$$

A partir de la [[Transacción#Notación|notación]] de las transacciones, podemos escribir por ejemplo:

$$
b_{T_1}b_{T_2}\dots R_{T_1}(X)\dots W_{T_2}(X)\dots c_{T_1}c_{T_2}
$$

## Ejecución Serial

Dado un conjunto de transacciones $T_1, T_2, \dots, T_n$, una **ejecución serial** es aquella en la que las transacciones se ejecutan por completo una detrás de otra, en algún orden dado.

Podemos calcular la cantidad de ejecuciones seriales distintas existen entre $n$ transacciones, como $n!$

## Serializabilidad

Decimos que un solapamiento de un conjunto de transacciones $T_1, T_2, \dots, T_n$ es **serializable** cuando la ejecución de sus instrucciones en dicho orden deja la base de datos en un estado equivalente a aquel en que la hubiera dejado alguna ejecución serial.

Nos interesa que los solapamientos producidos sean serializables, porque ellos garantizar la propiedad de aislamiento.

Deberíamos no solo mirar nuestra base de datos actual, sino cualquier estado inicial posible.

## Equivalencia de Solapamientos

Definimos la equivalencia a partir de un conjunto de solapamientos distintos del mismo conjunto de transacciones.

### Equivalencia de Resultados

Cuando, dado un estado inicial particular, ambos órdenes de ejecución dejan a la base de datos en el mismo estado, diremos que estamos ante equivalencia de resultados.

### Equivalencia de Conflictos

Cuando ambos órdenes de ejecución poseen los mismos [[Base de Datos/Concurrencia#Conflictos|conflictos]] entre instrucciones, diremos que estamos ante equivalencia de conflictos.

Esta noción es interesante, pues no depende del estado inicial de la base de datos. La equivalencia de conflictos implica equivalencia de resultados.

### Equivalencia de Vistas

Cuando en cada orden de ejecución, cada lectura $R_{T_i}(X)$ lee el valor escrito por la misma transacción $j$, en $W_{T_j}(X)$.

Además, se pide que en ambos órdenes la última modificación de cada ítem $X$ haya sido hecha por la misma transacción.

## Conflictos

Dado un orden de ejecución, un **conflicto** es un par de instrucciones $(I_1, I_2)$ ejecutadas por dos transacciones distintas $T_i$ y $T_j$, sobre un mismo ítem $X$ tales que $I_2$ se encuentra más tarde que $I_1$, y al menos una de las dos instrucciones es una **escritura**.

Todo par de instrucciones consecutivas de un solapamiento que no constituye un conflicto puede ser **invertido** en su ejecución. Esto obtiene un solapamiento equivalente por conflictos al inicial.

## Grafo de Precedencias

Una serializabilidad por conflictos puede ser evaluada a través del **grafo de precedencias**.

Dado un conjunto de transacciones $T_1, T_2, \dots, T_n$ que acceden a determinados ítems $X_1, X_2, \dots, X_p$, el grafo de precedencias es un grafo dirigido simple que se construye de la siguiente forma:

- Se crea un nodo por cada transacción
- Se agrega un arco entre los nodos $T_i, T_j$ (en ese orden) si y solo si existe algún conflicto entre dos instrucciones $I_{T_i}, I_{T_j}$.

Opcionalmente, podemos etiquetar el arco con el nombre del recurso que causa el conflicto.

Cada arco $(T_i, T_j)$ en el grafo representa una precedencia entre $T_i, T_j$ e indica que para que el resultado sea equivalente por conflictos a una ejecución serial, entonces en $T_i$ debe **preceder** a $T_j$.

Un orden de ejecución es serializable por conflictos si y solo si su grafo de precedencias es **acíclico**.

Si un orden de ejecución es serializable por conflictos, el orden de ejecución serial equivalente puede ser calculado a partir del grafo de precedencias, utilizando el algoritmo de **ordenamiento topológico**.
