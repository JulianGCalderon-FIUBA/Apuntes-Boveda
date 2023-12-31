Neo4j es una de las bases de datos orientadas a grafos más conocidas. Es actualmente utilizada por empresas como Cisco, HP, y Huawei.

Incluye soporte para transacciones ACID, y para bases de datos distribuidas.

Está desarrollada en Java, y posee APIs en distintos lenguajes como Python, Ruby, Java, etc.

Utiliza un lenguaje de consultas declarativo denominado **Cypher**.

## Creación

Un nodo puede tener distintos *labels*, dentro de cada *label*, el nodo tendrá un conjunto de propiedades con determinados valores.

```Cypher
CREATE (pedro:Persona {nombre: 'Pedro', color: 'Azul'})
```

No existe una estructura rígida, por lo que podemos agregar distintas propiedades para un mismo *label*.

## Consultas

Para buscar un nodo o conjunto de nodos, utilizamos el comando `MATCH`.

```Cypher
MATCH (p:Persona {nombre: 'Maria'}) RETURN p.nombre
```

El resultado de la consulta es un conjunto de *records*, que podemos representar con una tabla.

También se puede aplicar condiciones de selección sobre las búsquedas con el comando `WHERE`.

```Cypher
MATCH (m:Persona) WHERE m.color='Verde' RETURN m
```

Como estamos utilizando directamente `RETURN m`, entonces nos devolverá un grafo, en lugar de un conjunto de registros.

## Interrelaciones

Podemos utilizar el comando `CREATE` para definir interrelaciones entre los nodos.

```Cypher
CREATE (juan)-[:AMIGO_DE]->(lucas),
       (lucas)-[:AMIGO_DE]->(maria),
       (juan)-[:ENEMIGO_DE]->(maria)
```

Podemos consultar entidades que cumplan con ciertas interrelaciones a partir del comando `MATCH`.

```Cypher
MATCH (n:Persona)-[:AMIGO_DE]-(m:Persona)-[:AMIGO_DE]-(o:Persona),
      (n:Persona)-[:ENEMIGO_DE]-(o:Persona),
RETURN DISTINCT n.nombre, o.nombre
```

Los grafos son siempre dirigidos, pero podemos ignorar la direccionalidad en las consultas utilizando `-` en lugar de `->`.

Con un $*$ en la interrelación, podemos indicar una cantidad indeterminada de saltos.

```Cypher
MATCH (juan:Persona {nombre:'Juan'})
      (luis:Persona {nombre:'Luis'})
      camino=(juan)-[:AMIGO_DE*]-(luis)
RETURN length(camino)
```

## Agregación

No es necesario indicar por qué elementos agrupamos, se agrupa por todos aquellos que no están en una función de agregación.

```Cypher
MATCH (p1:Persona)-[:AMIGO_DE]-(p2:Persona)
RETURN p1.nombre, count(p2) 
```
