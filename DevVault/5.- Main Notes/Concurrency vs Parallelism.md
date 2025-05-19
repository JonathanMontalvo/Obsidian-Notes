2025-05-17 17:19

status: ==**Completo**==

tags: [concurrencia, paralelismo, hilos, java, c#]

---
# Concurrencia vs Paralelismo

Aunque suelen usarse como sinónimos, **concurrencia** y **paralelismo** son conceptos distintos en el diseño de software que involucra múltiples tareas.

---
## 🧠 ¿Qué es la concurrencia?

Es la **capacidad de un sistema para manejar múltiples tareas "al mismo tiempo"** a través de la **intercalación de su ejecución**, incluso si se ejecutan en un solo núcleo.

> Es como tener una sola persona atendiendo muchas tareas alternadamente.

---
## ⚙️ ¿Qué es el paralelismo?

Es la capacidad de **ejecutar múltiples tareas literalmente al mismo tiempo** en distintos núcleos o procesadores.

> Es como tener **varias personas** ejecutando tareas **en paralelo**.

---
## 🧩 Tabla comparativa

| Característica             | Concurrencia                                 | Paralelismo                                |
|----------------------------|-----------------------------------------------|--------------------------------------------|
| Objetivo                   | Manejar múltiples tareas                     | Ejecutar múltiples tareas a la vez         |
| Núcleos necesarios         | Uno (puede trabajar en un solo núcleo)       | Requiere múltiples núcleos                 |
| Ejecución simultánea real | No necesariamente                            | Sí                                         |
| Ideal para                | Tareas I/O-bound (espera, lectura, red)      | Tareas CPU-bound (procesamiento intensivo) |
| Ejemplo                    | Servidor web que atiende muchos usuarios     | Procesar imágenes o cálculos matemáticos   |
| Técnicas comunes           | Threads, async/await, Task                   | Parallel.For, PLINQ, Parallel Streams      |

---
## 📌 Analogía simple

- **Concurrencia**: 1 cocinero preparando 5 platos al mismo tiempo, turnándose entre ellos.
- **Paralelismo**: 5 cocineros, cada uno con su propio plato.

---
## ✅ Cuándo usar cada uno

|Necesidad|Opción recomendada|
|---|---|
|Muchas operaciones de red o I/O|Concurrencia|
|Procesamiento de grandes volúmenes de datos|Paralelismo|
|Mejora de tiempo de respuesta en UI|Concurrencia|
|Maximizar uso de CPU|Paralelismo|

---
## ☠️ Errores comunes

- Usar paralelismo en tareas que no lo requieren → **sobrecarga de hilos**.
- Suponer que concurrencia = ejecución en paralelo → **falso en hardware de un solo núcleo**.
- Olvidar sincronizar acceso a recursos compartidos → **condiciones de carrera y errores impredecibles**.

---
# References
- [Difference between Concurrency and Parallelism - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-concurrency-and-parallelism/)
- [Java Concurrency and Parallelism - Oracle Docs](https://docs.oracle.com/javase/tutorial/essential/concurrency/)
- [Parallel Programming in C# - Microsoft Docs](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/)