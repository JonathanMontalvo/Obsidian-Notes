2025-05-17 13:47

status: ==**Completo**==

tags:[paradigmas, java, c#, oop]

---
# What is polymorphism
El **polimorfismo** es un principio de la Programación Orientada a Objetos que permite que un mismo método o función pueda comportarse de distintas formas según el contexto.

Se manifiesta principalmente de dos maneras:
1. **Sobrecarga de métodos (Overloading):**  
   Definir varios métodos con el mismo nombre pero con diferentes parámetros dentro de la misma clase.
2. **Sobreescritura de métodos (Overriding):**  
   Modificar el comportamiento de un método heredado de una superclase en una subclase.

---
# 1. Sobrecarga de métodos (Overloading)
La **sobrecarga de métodos** es un tipo de polimorfismo **en tiempo de compilación** (polimorfismo estático) que permite definir varios métodos con el **mismo nombre** dentro de una misma clase, pero que se diferencian en la **lista de parámetros**.
## Características:
- Cambian el número de parámetros, o
- Cambian el tipo de parámetros, o
- Cambian ambos (tipo y número).
- El tipo de retorno puede ser igual o distinto, pero no es suficiente para diferenciar los métodos.
## Ventajas:
- Mejora la legibilidad del código al usar un nombre coherente para funciones relacionadas.
- Permite realizar la misma operación con diferentes tipos o cantidades de datos.
---
# 2. Sobreescritura de métodos (Overriding)
La **sobreescritura de métodos** es un tipo de polimorfismo **en tiempo de ejecución** (polimorfismo dinámico) que permite a una **subclase** redefinir la implementación de un método que ya está definido en su **superclase**.
## Características:
- El método debe existir en la superclase y la subclase.
- La firma del método (nombre, tipo y número de parámetros) debe ser la misma.
- En algunos lenguajes (como C#), el método de la superclase debe estar marcado como `virtual` para permitir la sobreescritura.
- Se usa para modificar o extender el comportamiento heredado.
## Ventajas:
- Permite implementar comportamientos específicos en clases derivadas manteniendo una interfaz común.
- Fundamental para el polimorfismo dinámico, donde el método que se ejecuta depende del tipo real del objeto en tiempo de ejecución.
---
# Diferencias clave entre Overloading y Overriding

|Aspecto|Sobrecarga (Overloading)|Sobreescritura (Overriding)|
|---|---|---|
|Polimorfismo|Estático (compilación)|Dinámico (ejecución)|
|Contexto|Dentro de la misma clase|Entre clase base y subclase|
|Firma del método|Diferente (tipo o número de parámetros)|Igual (misma firma)|
|Modificación del método|No modifica método existente|Modifica comportamiento heredado|
|Uso típico|Mismo método con diferentes entradas|Implementación específica en subclase|

---
# Example

### 1. Sobrecarga de métodos (Overloading)
```java
public class Calculadora {
    // Suma dos enteros
    public int sumar(int a, int b) {
        return a + b;
    }

    // Suma dos números decimales
    public double sumar(double a, double b) {
        return a + b;
    }

    // Suma tres enteros
    public int sumar(int a, int b, int c) {
        return a + b + c;
    }
}
```

```c#
public class Calculadora {
    public int Sumar(int a, int b) {
        return a + b;
    }

    public double Sumar(double a, double b) {
        return a + b;
    }

    public int Sumar(int a, int b, int c) {
        return a + b + c;
    }
}
```
### 2. Sobreescritura de métodos (Overriding)
```java
public class Animal {
    public void hacerSonido() {
        System.out.println("Sonido genérico");
    }
}

public class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau");
    }
}
```

```c#
public class Animal {
    public virtual void HacerSonido() {
        Console.WriteLine("Sonido genérico");
    }
}

public class Perro : Animal {
    public override void HacerSonido() {
        Console.WriteLine("Guau");
    }
}
```
---
# References
- [Polimorfismo en Java - Oracle](https://docs.oracle.com/javase/tutorial/java/IandI/polymorphism.html)
- [Polimorfismo en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/polymorphism)