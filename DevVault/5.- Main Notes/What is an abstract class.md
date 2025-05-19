2025-05-17 14:09

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is an abstract class
Una **clase abstracta** es una clase que **no puede ser instanciada directamente**.  
Sirve como una **plantilla base** para otras clases, definiendo una estructura común que las clases hijas deben seguir.

> Se declara con la palabra clave `abstract`.
## Características
- Puede contener:
  - Métodos abstractos (sin implementación)
  - Métodos concretos (con implementación)
  - Atributos y constructores
- Obliga a las clases hijas a **implementar los métodos abstractos**.
- Se usa comúnmente para definir comportamientos generales que serán refinados en las subclases.
## Diferencia con interfaces

| Clase Abstracta                   | Interface                         |
|----------------------------------|-----------------------------------|
| Puede tener código implementado  | Solo define métodos sin cuerpo (hasta C# 8) |
| Puede tener atributos y constructores | No puede tener atributos de instancia |
| Se usa para modelar jerarquías   | Se usa para definir contratos     |
| Solo se puede heredar de una     | Se pueden implementar varias      |

---
# Example
```java
public abstract class Animal {
    protected String nombre;

    public Animal(String nombre) {
        this.nombre = nombre;
    }

    public abstract void hacerSonido();

    public void comer() {
        System.out.println(nombre + " está comiendo.");
    }
}

public class Perro extends Animal {
    public Perro(String nombre) {
        super(nombre);
    }

    @Override
    public void hacerSonido() {
        System.out.println(nombre + " dice: ¡Guau!");
    }
}

public class Programa {
    public static void main(String[] args) {
        Perro miPerro = new Perro("Max");
        miPerro.hacerSonido(); // Max dice: ¡Guau!
        miPerro.comer();       // Max está comiendo.
    }
}
```

```c#
public abstract class Animal {
    public string Nombre { get; set; }

    public Animal(string nombre) {
        Nombre = nombre;
    }

    public abstract void HacerSonido();

    public void Comer() {
        Console.WriteLine($"{Nombre} está comiendo.");
    }
}

public class Perro : Animal {
    public Perro(string nombre) : base(nombre) {}

    public override void HacerSonido() {
        Console.WriteLine($"{Nombre} dice: ¡Guau!");
    }
}

class Programa {
    static void Main() {
        Perro miPerro = new Perro("Max");
        miPerro.HacerSonido(); // Max dice: ¡Guau!
        miPerro.Comer();       // Max está comiendo.
    }
}
```

---
# References
- [Oracle Docs - abstract (Java)](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)
- [Microsoft Docs - abstract (C#)](https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/keywords/abstract)