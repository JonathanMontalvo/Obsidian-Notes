2025-05-17 17:03

status: ==**Completo**==

tags: [concurrencia, hilos, java, c#]

---
# ¿Qué es la Concurrencia?

La **concurrencia** es la capacidad de un programa para **ejecutar múltiples tareas (o partes de código) de forma aparentemente simultánea**.

> La concurrencia **no significa necesariamente que las tareas se ejecutan al mismo tiempo**, sino que el sistema puede **cambiar rápidamente de una tarea a otra**, dando la **ilusión de paralelismo.**

En sistemas con múltiples núcleos o procesadores, la concurrencia puede llevarse más allá con **paralelismo real**, donde varias tareas se ejecutan **en paralelo**.

---
## Diferencia entre concurrencia y paralelismo

| Concepto       | Descripción                                                                 |
|----------------|-----------------------------------------------------------------------------|
| Concurrencia   | Gestiona múltiples tareas al mismo tiempo (aunque no necesariamente en paralelo). |
| Paralelismo    | Ejecuta múltiples tareas **exactamente al mismo tiempo** en distintos núcleos.     |

---
## ¿Para qué se usa?

- Mejorar la **responsividad** (ej. interfaces gráficas)
- Aprovechar **recursos multinúcleo**
- Ejecutar **tareas pesadas en segundo plano**
- Realizar **I/O asincrónico** sin bloquear la ejecución

---
## Formas de lograr concurrencia

### 🧵 Hilos (Threads)
Ejecutan bloques de código de forma independiente.

### ⏳ Tareas (Tasks)
Abstracciones modernas para manejar trabajo concurrente sin lidiar con hilos directamente.

### 🌀 Async/Await
Permiten escribir código asíncrono de forma sencilla y legible (disponible en C# y Java moderno con `CompletableFuture` o `async` de terceros).

---
## Problemas comunes
- **Condiciones de carrera**: cuando dos hilos acceden a la misma variable al mismo tiempo.
- **Bloqueos (deadlocks)**: cuando dos hilos esperan el uno al otro para liberar recursos.
- **Interbloqueos y hambre de recursos**: errores de diseño donde algunos hilos nunca se ejecutan.

---
## Mecanismos para controlar concurrencia

| Lenguaje | Mecanismos de sincronización                           |
| -------- | ------------------------------------------------------ |
| Java     | `synchronized`, `ReentrantLock`, `volatile`, `Atomic*` |
|C#|`lock`, `Monitor`, `Mutex`, `Semaphore`, `volatile`|

---
# Example
```java
public class MiHilo extends Thread {
    public void run() {
        System.out.println("Hola desde un hilo");
    }
}
// Uso
MiHilo hilo = new MiHilo();
hilo.start();

Runnable tarea = () -> System.out.println("Desde runnable");
new Thread(tarea).start();

ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(() -> System.out.println("Desde thread pool"));
executor.shutdown();
```

```c#
Thread hilo = new Thread(() => Console.WriteLine("Desde un hilo"));

hilo.Start();
await Task.Run(() => {
    Console.WriteLine("Desde una Task");
});

async Task ProcesarAsync() {
    await Task.Delay(1000);
    Console.WriteLine("Tarea asincrónica completada");
}
```

## Sincronización
 ```java
 public class Contador {
    private int cuenta = 0;

    public synchronized void incrementar() {
        cuenta++;
    }
}
``` 

```c#
class Contador {
    private int cuenta = 0;
    private readonly object bloqueo = new object();

    public void Incrementar() {
        lock (bloqueo) {
            cuenta++;
        }
    }
}
```
---
# References
- [Java Concurrency Tutorial (Oracle)](https://docs.oracle.com/javase/tutorial/essential/concurrency/)
- [Asynchronous programming with async and await (C#)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/)
- Multithreading in Java - Baeldung
- [Task Parallel Library (TPL) - Microsoft Docs](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/task-parallel-library-tpl-overview)