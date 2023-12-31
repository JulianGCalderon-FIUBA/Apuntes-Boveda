## Tipo de Dato

Un tipo de dato define dos cosas importantes:

1. El conjunto de todos los valores posibles que una variable de ese tipo puede tomar
2. Las operaciones que las variables de ese tipo de dato pueden utilizar

Los lenguajes de programación tienen tipos de datos **primitivos**, los cuales son predefinidos por el lenguaje de programación.

![[TDA 1693351689.png|525]]

## Abstracción

Proviene del latín *abstractio*, y significa: separar aisladamente en la mente las características de un objeto o un hecho, dejando de prestar atención al mundo sensible para enfocarse solo en el pensamiento.

Separamos lo que nos **importa**, y nos olvidamos de lo **innecesario**

![[TDA 1693351689-1.png|450]]

En la imagen se ve una demostración de Picasso del concepto de abstracción.

## Tipo de Dato Abstracto

Un tipo de dato abstracto *(TDA),* es una clase de objetos abstractos, los cuales están caracterizados por las operaciones que definimos sobre esos objetos. Cuando un programador utiliza un TDA, está únicamente interesado en el comportamiento del objeto (¿Qué?), y no de como se implementa. La visión de aquel que utiliza un TDA es exclusivamente de **Caja Negra**.

### El Qué y el Cómo

Las visiones de caja negra y caja blanca hacen una gran diferencia:

- El **Qué:** Este se refiere a la funcionalidad del TDA, relacionado con ¿Qué hace esto? No le interesa como se implementa, por lo que se denomina **caja negra**.
- El **Cómo:** Este se refiere a como se implemente el TDA, relacionado con ¿Cómo hace esto? De forma análoga, se denomina **caja blanca**.

En el estudio e implementación de los TDA es fundamental poder separar correctamente el **qué** y el **cómo**.

**Un qué y mil cómos:** Este concepto hace referencia a que, para cada problema a resolver, hay infinitas maneras de hacerlo.

### El Contrato

El contrato es el medio de comunicación entre el cliente y el programador, acá se define exactamente lo que tiene que realizar el TDA. Una vez definido el contrato, es momento de diseñar e implementar.

### Ventajas

La utilización de TDA tiene muchas ventajas a la hora de realizar programas de gran tamaño:

- **Manejan la Abstracción:** Esto permite simplificar la realidad mediante la simplificación, despojando la complejidad que no es importante para el problema.
- **Encapsulamiento:** La información que no debe usar el usuario están ocultas, él solo tiene acceso a las funciones que el mismo entiende y necesita.
- **Localización del Cambio:** Cuando existe un error en el programa, es más fácil arreglarlo si el código se encuentra modularizado, ya que podemos probar cada parte del programa por separado.

## Proceso de Desarrollo de Software

**El software no se fabrica, el software se desarrolla**. El desarrollo de software no es una única tarea, sino que incluye a un conjunto de etapas:

- **Análisis:** En esta etapa, debemos comprender el problema. Determinar aquellas cosas que se requiere para la resolución del mismo. ¿Qué hay que hacer?
- **Diseño:** Consiste en crear una solución, teniendo en cuenta los múltiples aspectos del software y del hardware. ¿Cómo hay que hacer?
- **Implementación:** Es la etapa más conocida, en la que se desarrolla software en sí
- **Pruebas:** Para verificar que el software que desarrollamos funciona correctamente, entonces debemos probarlo.
- **Instalación:** Esta etapa se basa en hacer que el software esté andando
- **Mantenimiento:** El software es un producto susceptible al cambio, a mejoras, a la reparación. Esta etapa se ocupa de esto.
