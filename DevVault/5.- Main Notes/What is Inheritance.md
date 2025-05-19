2025-05-17 13:20

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is Inheritance
La **herencia** es un mecanismo fundamental de la Programación Orientada a Objetos (POO) que permite que una clase (llamada **clase derivada** o **subclase**) herede atributos y métodos de otra clase (llamada **clase base** o **superclase**).

> Facilita la reutilización de código y la creación de jerarquías entre clases.

### Características clave:
- La subclase hereda las propiedades y comportamientos de la superclase.
- La subclase puede agregar nuevas propiedades o métodos, o sobrescribir (override) los existentes.
- Permite el polimorfismo: un objeto de la subclase puede ser tratado como un objeto de la superclase.

---
# Example
```java
public class Animal {
    protected String nombre;
    protected int edad;

    public Animal(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void hacerSonido() {
        System.out.println("Sonido genérico");
    }

    public void mostrarInfo() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }
}

public class Perro extends Animal {
    private String raza;

    public Perro(String nombre, int edad, String raza) {
        super(nombre, edad);  // Llamada al constructor de la superclase
        this.raza = raza;
    }

    @Override
    public void hacerSonido() {
        System.out.println("Guau");
    }

    public void mostrarRaza() {
        System.out.println("Raza: " + raza);
    }
}
```

```c#
public class Animal {
    protected string Nombre;
    protected int Edad;

    public Animal(string nombre, int edad) {
        Nombre = nombre;
        Edad = edad;
    }

    public virtual void HacerSonido() {
        Console.WriteLine("Sonido genérico");
    }

    public void MostrarInfo() {
        Console.WriteLine($"Nombre: {Nombre}, Edad: {Edad}");
    }
}

public class Perro : Animal {
    private string Raza;

    public Perro(string nombre, int edad, string raza) : base(nombre, edad) {
        Raza = raza;
    }

    public override void HacerSonido() {
        Console.WriteLine("Guau");
    }

    public void MostrarRaza() {
        Console.WriteLine($"Raza: {Raza}");
    }
}

```
---
# References
- [Herencia en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html)
- [Herencia en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/inheritance)