Un *stream* es una lista cuyo último elemento aún no está definido, es una lista sin fin. Esto permite que la lista se expanda posteriormente a ser definida, ya sea manualmente o a través de una función recursiva.

```Oz
local A B C in
	A = 1|2|3|B
	B = 4|5|6|C
	C = 7|8|9|nil
end
```

## Productor Consumidor

Esto puede ser utilizado para comunicar hilos. Un hilo expande progresivamente una lista, mientras que otro hilo tome los valores a medida que se van generando.

```Oz
local Produce Consume L in
	Produce = proc {$ N Limit L}
		{Time.delay 500}
		if N < Limit then
			local T in
				L = N|T
				{Produce N+1 Limit T}
			end
		end
	end
	
	Consume = proc {$ L}
		case L of H|T then
			if H mod 2 == 0 then
				{Browse H}
			end
				{Consume T}
			end
	end
	
	thread {Produce 0 10 L} end
	thread {Consume L} end
end
```

## Demand Driven Concurreny

En el problema anterior, puede surgir el problema de que el consumidor no tome recurso a la misma velocidad que se produce.

Para solucionar esto, podemos hacer que el consumidor le indique al productor cuando producir. El consumidor crea un nuevo elemento vacío, y el productor le da un valor.

## Bounded Buffer

El productor produce elementos, pero con un límite. No debe esperar a que el productor necesite un elemento, pero tampoco puede producir indefinidamente.

## Múltiples Productores

Si queremos tener múltiples productores, entonces puede haber problemas de concurrencia. Para resolverlo, necesitaremos [[Teoría de Lenguaje/Canales|canales]].
