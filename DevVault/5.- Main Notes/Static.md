2025-05-17 14:10

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# Static
La palabra clave **`static`** indica que un **miembro (atributo, método o clase interna)** pertenece a la **clase en sí**, y no a una instancia (objeto) específica.

> Se puede acceder a elementos `static` sin necesidad de crear un objeto de la clase.

## Características principales
- Los miembros `static` **comparten una sola copia** entre todas las instancias de la clase.
- Se accede a ellos con: `NombreClase.Miembro`.
- No pueden usar `this`, ya que no pertenecen a ninguna instancia.
- Se usan frecuentemente para:
  - Constantes globales
  - Contadores o estados compartidos
  - Métodos utilitarios
---
## ¿Dónde se puede usar `static`?

| Elemento            | C#  | Java |
|---------------------|-----|------|
| Atributos/Variables | ✅  | ✅   |
| Métodos             | ✅  | ✅   |
| Clases internas     | ✅  | ✅   |
| Constructores       | ❌  | ❌   |
| Clases externas     | ✅\*| ❌   |

\* En C#, las clases externas pueden ser estáticas si todos sus miembros también lo son (`static class`).

## Limitaciones
- Un método `static` **solo puede acceder** a otros miembros `static`.
- No puede acceder directamente a atributos o métodos de instancia.
---
# ¿Cuándo usar `static`?

✅ Cuando el dato o comportamiento:
- No depende de una instancia específica.
- Representa un valor común/global.
- Es una función utilitaria o auxiliar.

❌ Evítalo cuando:
- Necesitas trabajar con datos de instancia.
- Requieres polimorfismo o herencia (no se puede overridear un método `static`).
---
# Example
```java
public class Matematicas {
    public static final double PI = 3.1416;

    public static int sumar(int a, int b) {
        return a + b;
    }
}

public class Programa {
    public static void main(String[] args) {
        System.out.println(Matematicas.PI);         // 3.1416
        System.out.println(Matematicas.sumar(4, 5)); // 9
    }
}

public class Persona {
    public static int TotalPersonas = 0;

    public Persona() {
        TotalPersonas++;
    }
}
```

```c#
public class Matematicas {
    public static double PI = 3.1416;

    public static int Sumar(int a, int b) {
        return a + b;
    }
}

class Programa {
    static void Main() {
        Console.WriteLine(Matematicas.PI);         // 3.1416
        Console.WriteLine(Matematicas.Sumar(4, 5)); // 9
    }
}

public static class Utilidades {
    public static void MostrarMensaje(string mensaje) {
        Console.WriteLine(mensaje);
    }
}

```

---
# References
- [Oracle Docs - Understanding Class Members (Java)](https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html)
- [Microsoft Docs - static (C#)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/static)