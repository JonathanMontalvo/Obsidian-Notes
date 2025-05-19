2025-05-17 14:10

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# Access modifiers
Los **modificadores de acceso** controlan la **visibilidad** o **acceso** a clases, métodos, atributos y otros miembros dentro del código.

> Son esenciales para la **encapsulación**, ya que permiten ocultar detalles internos y exponer solo lo necesario.

---
## Tipos de modificadores (C# y Java)

| Modificador     | C#             | Java           | Acceso desde...                      |
|-----------------|----------------|----------------|--------------------------------------|
| `public`        | ✅              | ✅              | En cualquier parte                   |
| `private`       | ✅              | ✅              | Solo dentro de la misma clase        |
| `protected`     | ✅              | ✅              | Clase actual + subclases             |
| `internal`      | ✅              | ❌              | Dentro del mismo ensamblado (proyecto) |
| `protected internal` | ✅        | ❌              | Subclases o mismo ensamblado         |
| `private protected`  | ✅        | ❌              | Solo subclases dentro del mismo ensamblado |
| (default)       | ❌ (no existe)  | ✅ (`package-private`) | Solo dentro del mismo paquete     |

---
## ¿Cuándo usar cada uno?

- `public`: cuando quieres que algo sea accesible **desde cualquier lugar**.
- `private`: para encapsular y proteger datos internos.
- `protected`: para permitir que **solo las subclases** accedan.
- `internal` (C#): para uso dentro de un mismo ensamblado/proyecto.
- (default en Java): útil para **modularizar por paquete** sin exponer al resto.
---
# Example
```java
public class Persona {
    private String nombre;
    protected int edad;
    public String nacionalidad;

    void mostrarPaquete() { // default (package-private)
        System.out.println("Visible solo dentro del paquete.");
    }

    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void mostrar() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }
}
```

```c#
public class Persona {
    private string nombre;
    protected int edad;
    public string Nacionalidad { get; set; }

    internal void MostrarInterno() {
        Console.WriteLine("Visible solo dentro del proyecto.");
    }

    protected internal void MostrarProtegidoInterno() {
        Console.WriteLine("Visible en subclases o dentro del mismo ensamblado.");
    }

    public Persona(string nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void Mostrar() {
        Console.WriteLine($"Nombre: {nombre}, Edad: {edad}");
    }
}
```
---
# References
- [Oracle Docs - Controlling Access to Members of a Class (Java)](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)
- [Microsoft Docs - Access Modifiers (C#)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)