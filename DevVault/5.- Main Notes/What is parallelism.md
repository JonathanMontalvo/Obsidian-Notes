2025-05-17 17:10

status: ==**Completo**==

tags: [paralelismo, hilos, java, c#]

---
# ¿Qué es el Paralelismo?

El **paralelismo** es un modelo de ejecución en el que **varias tareas se ejecutan literalmente al mismo tiempo**, aprovechando **múltiples núcleos de CPU**.  
A diferencia de la **concurrencia**, donde las tareas pueden turnarse en un solo núcleo, en el paralelismo **cada núcleo puede ejecutar una tarea distinta al mismo tiempo**.

> 🔁 Concurrencia: gestionar muchas tareas al mismo tiempo.  
> 🧩 Paralelismo: **ejecutar** muchas tareas al mismo tiempo.

---
## ¿Por qué es útil?

- Mejora el **rendimiento** en tareas pesadas.
- Aprovecha el **hardware multinúcleo**.
- Es ideal para tareas **independientes** que pueden ejecutarse sin depender unas de otras (como procesamiento de datos, cálculos matemáticos, simulaciones, etc).

---
## Tipos de paralelismo

| Tipo                       | Descripción                                                       |
|----------------------------|-------------------------------------------------------------------|
| Paralelismo a nivel de datos | Ejecutar la misma operación sobre distintos datos en paralelo     |
| Paralelismo a nivel de tareas | Ejecutar diferentes tareas simultáneamente                        |

---
## ¿Cuándo usar paralelismo?

- Cuando tienes operaciones **CPU intensivas**.
- Cuando las tareas **no dependen entre sí**.
- Cuando puedes dividir un problema en **subproblemas independientes**.

---
## Consideraciones

- El paralelismo **no siempre mejora el rendimiento** si hay mucha sincronización o bloqueo entre tareas.
- Hay una **sobrecarga** al crear hilos o tareas, así que no siempre es más rápido.
- No es ideal para **operaciones I/O-bound**, que se benefician más de **asincronía**.

---
## Problemas comunes en paralelismo

- **Sincronización**: cuando varias tareas acceden a recursos compartidos.
- **Contención**: múltiples hilos compitiendo por el mismo recurso.
- **Overhead de hilos**: crear demasiados hilos puede ser contraproducente.
- **No determinismo**: el orden de ejecución no siempre es predecible.

---
## Buenas prácticas

- Usa **paralelismo solo cuando el problema realmente lo necesita**.
- Evita **operaciones dependientes entre tareas**.
- Usa **colecciones thread-safe** cuando compartas datos.
- Medir y **probar el rendimiento real**, no asumir mejoras automáticas.

---
# Example
## Paralelismo en Java
#### 🧩 ForkJoinPool
```java
ForkJoinPool pool = new ForkJoinPool();
pool.submit(() -> IntStream.range(0, 10).parallel().forEach(System.out::println));
pool.shutdown();
```
#### 🧩 Parallel Streams (Java 8+)
```java
List<Integer> lista = Arrays.asList(1, 2, 3, 4, 5, 6);
lista.parallelStream()
     .map(n -> n * n)
     .forEach(System.out::println);

```
## Paralelismo en C#  
#### 🧩 Parallel.For
```c#
Parallel.For(0, 10, i => {
    Console.WriteLine($"Índice: {i}, Thread: {Thread.CurrentThread.ManagedThreadId}");
});
```
#### 🧩 Parallel.Invoke
```c#
Parallel.Invoke(
    () => Metodo1(),
    () => Metodo2(),
    () => Metodo3()
);
```
#### 🧠 PLINQ (Parallel LINQ)
```c#
var resultado = datos
    .AsParallel()
    .Where(n => n % 2 == 0)
    .ToList();
```
---
# References
- [Parallel Programming in .NET](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/)
- [Fork/Join Framework (Oracle)](https://docs.oracle.com/javase/tutorial/essential/concurrency/forkjoin.html)