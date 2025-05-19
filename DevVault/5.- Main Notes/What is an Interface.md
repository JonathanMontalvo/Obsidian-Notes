2025-05-17 13:20

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is an Interface
Una **interface** es un contrato o un conjunto de métodos y propiedades que una clase debe implementar sin definir su comportamiento.  
Define **qué** debe hacer una clase, pero no **cómo** hacerlo.

> Las interfaces permiten definir funcionalidades comunes que pueden ser implementadas por diferentes clases, favoreciendo la abstracción y el desacoplamiento.

### Características principales:
- Solo declara métodos y propiedades, sin implementación (en la mayoría de los lenguajes).
- Una clase puede implementar múltiples interfaces (multiples herencia de tipo).
- Promueven la **polimorfía** y la **flexibilidad** en el diseño de software.
---
# Example
```java
public interface Vehiculo {
    void acelerar();
    void frenar();
}

public class Coche implements Vehiculo {
    @Override
    public void acelerar() {
        System.out.println("El coche acelera");
    }

    @Override
    public void frenar() {
        System.out.println("El coche frena");
    }
}
```

```c#
public interface IVehiculo {
    void Acelerar();
    void Frenar();
}

public class Coche : IVehiculo {
    public void Acelerar() {
        Console.WriteLine("El coche acelera");
    }

    public void Frenar() {
        Console.WriteLine("El coche frena");
    }
}
```
---
# References
- [Interfaces en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)
- [Interfaces en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/interfaces/)