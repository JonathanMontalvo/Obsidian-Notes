2025-05-17 13:18

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is a Class
Una **clase** es una plantilla o modelo a partir del cual se crean objetos en la Programación Orientada a Objetos (POO).  
Define un conjunto de atributos y métodos comunes a todos los objetos de ese tipo.

> **Clase = Definición / Objeto = Instancia de esa definición**

Una clase encapsula:
- **Propiedades** (estado): Variables que describen las características del objeto.
- **Métodos** (comportamiento): Funciones que definen lo que el objeto puede hacer.

### Relación con el objeto
- La clase no ocupa memoria hasta que se crea un objeto (instancia).
- Un objeto es una realización concreta de una clase.

---
# Example
```java
public class Persona {
    public string Nombre;
    public int Edad;

    public void Saludar() {
        System.out.println("Hola, soy " + nombre);
    }
}
```

---
# References
- [Clases en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html)
- [Clases en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/classes)
    