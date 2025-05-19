2025-05-17 14:02

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# Constructor Method
Un **constructor** es un método especial que se ejecuta automáticamente cuando se crea una instancia (objeto) de una clase.  

Su función principal es **inicializar los atributos del objeto**.
> Un constructor **no tiene tipo de retorno**, ni siquiera `void`, y su nombre debe coincidir con el nombre de la clase.
---
## Tipos de constructores

#### 1. Constructor por defecto (default)
- No recibe parámetros.
- Si no defines uno, el compilador genera uno automáticamente.
#### 2. Constructor con parámetros
- Permite inicializar los atributos del objeto con valores específicos al momento de instanciarlo.

#### 3. Sobrecarga de constructores
- Puedes definir varios constructores con diferente lista de parámetros para ofrecer distintas formas de crear objetos.
---
# Example
```java
public class Persona {
    private String nombre;
    private int edad;

    // Constructor por defecto
    public Persona() {
        this.nombre = "Sin nombre";
        this.edad = 0;
    }

    // Constructor con parámetros
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    public void mostrarDatos() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }
}
Persona p1 = new Persona(); // Usa el constructor por defecto
Persona p2 = new Persona("Ana", 25); // Usa el constructor con parámetros
```

```c#
public class Persona {
    private string Nombre;
    private int Edad;

    // Constructor por defecto
    public Persona() {
        Nombre = "Sin nombre";
        Edad = 0;
    }

    // Constructor con parámetros
    public Persona(string nombre, int edad) {
        Nombre = nombre;
        Edad = edad;
    }

    public void MostrarDatos() {
        Console.WriteLine($"Nombre: {Nombre}, Edad: {Edad}");
    }
}
Persona p1 = new Persona(); // Constructor por defecto
Persona p2 = new Persona("Ana", 25); // Constructor con parámetros

```
---
# References
- [Constructores en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)
- [Constructores en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/constructors)