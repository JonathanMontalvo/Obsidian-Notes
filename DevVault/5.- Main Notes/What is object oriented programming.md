2025-05-17 13:09

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# Object Oriented Programming (OOP)
La **Programación Orientada a Objetos (POO)** es un paradigma que organiza el código en torno a **objetos**, los cuales son instancias de **clases**. Cada objeto contiene **atributos** (datos) y **métodos** (comportamientos).

Este enfoque busca representar entidades del mundo real y facilita la reutilización, escalabilidad y mantenimiento del código. Sus **principios fundamentales** son:

- **Encapsulamiento**: ocultar los detalles internos de un objeto.
- **Abstracción**: representar solo los aspectos relevantes.
- **Herencia**: reutilizar atributos y comportamientos en clases hijas.
- **Polimorfismo**: permitir que objetos se comporten de manera distinta según el contexto.


---
# Example

```java
// Ejemplo de Programación Orientada a Objetos en Java

// Clase que representa a un Perro
class Perro {
    // Atributos
    private String nombre;
    private int edad;

    // Constructor
    public Perro(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Método (comportamiento)
    public void ladrar() {
        System.out.println(nombre + " dice: ¡Guau!");
    }

    // Getters (encapsulamiento)
    public String getNombre() {
        return nombre;
    }

    public int getEdad() {
        return edad;
    }
}

// Clase principal
public class ProgramaOOP {
    public static void main(String[] args) {
        // Crear un objeto Perro
        Perro miPerro = new Perro("Firulais", 3);

        // Acceder a los métodos del objeto
        System.out.println("Nombre del perro: " + miPerro.getNombre());
        System.out.println("Edad del perro: " + miPerro.getEdad() + " años");
        miPerro.ladrar();
    }
}
```

---
# References
