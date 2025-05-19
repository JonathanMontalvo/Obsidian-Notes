2025-05-17 14:10

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# Generics
os **Generics** permiten escribir código **flexible, reutilizable y seguro** para trabajar con **tipos de datos no especificados hasta el momento de uso**. Son fundamentales para crear estructuras como listas, diccionarios, repositorios, clases utilitarias y más.

> Permiten trabajar con clases, interfaces, métodos y estructuras de forma que puedan operar con distintos tipos sin duplicar código.
---
## Ventajas

- Reutilización de código.
- Seguridad en tiempo de compilación.
- Evitan castings innecesarios.
- Mejor legibilidad y mantenibilidad.
---
## Aplicación de Generics

### 1. Clases genéricas  
Permiten definir atributos y comportamientos que se adaptan a distintos tipos sin duplicar código.
### 2. Métodos genéricos  
Métodos que aceptan o devuelven tipos genéricos, independientes del tipo de la clase.
### 3. Interfaces genéricas  
Útiles para construir contratos reutilizables para distintos tipos de datos.
### 4. Múltiples tipos  
Puedes declarar más de un parámetro de tipo (`<T1, T2>`).

---
## Restricciones de tipo
### En C# #
Puedes limitar los tipos genéricos con `where`:
- `where T : class` – Solo tipos de referencia
- `where T : struct` – Solo tipos de valor
- `where T : new()` – Debe tener constructor sin parámetros
- `where T : BaseClass` – Herencia de clase base
- `where T : IInterface` – Implementa interfaz

### En Java
Se usa `extends` para clases o interfaces:
- `T extends Number` – Acepta subtipos de Number
- No hay constructor genérico directo (`new()`), por limitaciones del type erasure.

---
## Covarianza y Contravarianza
### En Java  
Se usan **wildcards**:
- `?` → tipo desconocido
- `? extends T` → subtipos de T
- `? super T` → supertipos de T

### En C#  
Aplica a interfaces y delegados:
- `out T` → covarianza (solo salida)
- `in T` → contravarianza (solo entrada)
---
## Buenas prácticas
- Nombres estándar: `T`, `TKey`, `TValue`, `TResult`
- Usa restricciones para claridad
- No abuses si un tipo genérico no es necesario
- Agrupa lógica genérica para estructuras reutilizables
---
## Limitaciones

| Característica                        | Java         | C#               |
|--------------------------------------|--------------|------------------|
| Crear `new T()`                      | ❌           | ✅ (con `where`) |
| Crear array `new T[]`                | ❌           | ✅               |
| Acceder al tipo real (`T.class`)     | ❌           | ✅ (`typeof(T)`) |
| Herencia directa de tipo concreto    | Limitado     | Sí, con restricciones |

---
# Example
## Clase genérica

```java
public class Caja<T> {
    private T contenido;

    public void setContenido(T contenido) {
        this.contenido = contenido;
    }

    public void mostrarContenido() {
        System.out.println(contenido);
    }
}
```

```c#
public class Caja<T> {
    public T Contenido { get; set; }

    public void MostrarContenido() {
        Console.WriteLine(Contenido);
    }
}
```
## Método genérico
```java
public static <T extends Comparable<T>> T obtenerMayor(T a, T b) {
    return a.compareTo(b) > 0 ? a : b;
}
```

```c#
public static T ObtenerMayor<T>(T a, T b) where T : IComparable<T> {
    return a.CompareTo(b) > 0 ? a : b;
}
```
## Interfaz genérica
```java
public interface Repositorio<T> {
    void agregar(T entidad);
    T obtenerPorId(int id);
}
```

```c#
public interface IRepositorio<T> {
    void Agregar(T entidad);
    T ObtenerPorId(int id);
}
```
## Repositorio completo
```java
public class RepositorioMemoria<T> implements Repositorio<T> {
    private List<T> almacenamiento = new ArrayList<>();

    public void agregar(T entidad) {
        almacenamiento.add(entidad);
    }

    public T obtenerPorId(int id) {
        return almacenamiento.get(id);
    }
}
```

```c#
public class RepositorioMemoria<T> : IRepositorio<T> {
    private List<T> almacenamiento = new List<T>();

    public void Agregar(T entidad) {
        almacenamiento.Add(entidad);
    }

    public T ObtenerPorId(int id) {
        return almacenamiento[id];
    }
}
```
## Clase con múltiples tipos
```java
public class Par<T1, T2> {
    public T1 primero;
    public T2 segundo;
}
```

```c#
public class Par<T1, T2> {
    public T1 Primero { get; set; }
    public T2 Segundo { get; set; }
}
```
## Wildcards en Java
```java
public void imprimirLista(List<? extends Number> lista) {
    for (Number n : lista) {
        System.out.println(n);
    }
}
```
## Covarianza / Contravarianza en C# #
```c#
public interface IProductor<out T> {
    T Obtener();
}

public interface IConsumidor<in T> {
    void Procesar(T item);
}
```
## Funciones genéricas (delegados) en C# #
```c#
Func<int, string> convertir = numero => numero.ToString();
```
---
# References
- [Oracle Docs - Java Generics](https://docs.oracle.com/javase/tutorial/java/generics/)
- [Microsoft Docs - C# Generics](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/)