2025-05-17 13:19

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is an Object
Un **objeto** es una unidad fundamental en la Programación Orientada a Objetos (POO). Representa una entidad del mundo real y es una instancia de una clase.  
Cada objeto contiene:
- **Atributos** (también llamados *campos* o *propiedades*): Representan el estado del objeto.
- **Métodos** (también llamados *funciones*): Definen los comportamientos del objeto.

### Características clave de un objeto:
- **Identidad**: Cada objeto es único.
- **Estado**: Representado por sus atributos.
- **Comportamiento**: Definido por sus métodos.

En Java y C#, los objetos se crean utilizando la palabra clave `new` esta palabra nos ayuda a reservar un espacio de **Heap Memory**.

---
# Example
``` java
class Coche {
    public string Color;
    public int Velocidad;

    public void Acelerar() {
        Velocidad += 10;
    }
}

Coche miCoche = new Coche();
miCoche.Color = "Rojo";
miCoche.Acelerar();
```
---
# References
- [Conceptos OOP en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/concepts/)
- [Clases y Objetos en C# - Microsoft](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/classes)