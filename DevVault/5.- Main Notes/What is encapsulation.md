2025-05-17 13:29

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is encapsulation
La **encapsulación** es un principio fundamental de la Programación Orientada a Objetos (POO) que consiste en **ocultar los detalles internos** de un objeto y **proteger su estado**, permitiendo el acceso solo a través de métodos públicos (getters y setters).

> Se basa en la idea de que los objetos deben controlar su propio estado.

### Objetivos de la encapsulación:
- Proteger los datos contra modificaciones indebidas.
- Ocultar la complejidad interna.
- Favorecer el mantenimiento y la evolución del código.

### ¿Cómo se aplica?
1. Declarando los atributos como `private`.
2. Proporcionando métodos `public` para acceder (`get`) o modificar (`set`) esos atributos.

---
# Example
```java
public class CuentaBancaria {
    private double saldo;

    public double getSaldo() {
        return saldo;
    }

    public void setSaldo(double saldo) {
        if (saldo >= 0) {
            this.saldo = saldo;
        }
    }
}```
### **Full Property with Backing Field** (*Propiedad completa con campo privado*)

```c#
public class CuentaBancaria {
    private double _saldo;

    public double Saldo {
        get { return _saldo; }
        set { _saldo = value; }
    }
}
```
## **Auto-implemented Properties** (*Propiedades Auto-implementadas*)
```c#
public class CuentaBancaria {
    public double Saldo { get; set; }
}
```

---
# References
- [Encapsulación en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/encapsulation.html)
- [Encapsulación en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)