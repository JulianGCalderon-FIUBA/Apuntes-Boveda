La sección crítica se modeliza planteando un problema genérico, el cual luego se puede utilizar para analizar cualquier programa concurrente.

Cada proceso se ejecuta en un bucle infinito cuyo código puede dividirse en parte crítica y parte no crítica.

Especificamos las propiedades de corrección para este escenario:

- **Exclusión mutua:** No deben intercalarse instrucciones en la sección crítica
- **Ausencia de deadlock:** Si dos procesos están tratando de entrar a la sección crítica, eventualmente alguno de ellos debe tener éxito.
- **Ausencia de starvation:** Si un proceso trata de entrar a la sección crítica, eventualmente debe tener éxito.

Además, tendremos:

- La sección crítica debe progresar (finalizar eventualmente)
- La sección no-crítica no requiere progreso (puede terminar o entrar en un loop infinito).

## Solución con [[Semáforos]]

Podemos utilizar un semáforo binario (donde sus valores posibles son cero o uno). Estos se comportan igual que los *locks* de escritura.

```C
while true {
	// non-critical section
	wait(S)
	// critical section
	signal(S)
}
```
