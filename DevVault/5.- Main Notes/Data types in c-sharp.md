2025-05-17 11:26

status: ==**Completo**==

tags: [c#, arrays]

---
# Data types
En c# hay diferentes tipos de datos
### **1. Tipos de datos primitivos (Value Types)**

Son almacenados directamente en la memoria y no requieren instancias de objetos.

- **Números enteros**:
    
    - `byte` (8 bits, 0 a 255)
        
    - `sbyte` (8 bits, -128 a 127)
        
    - `short` (16 bits, -32,768 a 32,767)
        
    - `ushort` (16 bits, 0 a 65,535)
        
    - `int` (32 bits, -2,147,483,648 a 2,147,483,647)
        
    - `uint` (32 bits, 0 a 4,294,967,295)
        
    - `long` (64 bits, -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807)
        
    - `ulong` (64 bits, 0 a 18,446,744,073,709,551,615)
        
- **Números de punto flotante**:
    
    - `float` (32 bits, precisión de ~7 dígitos)
        
    - `double` (64 bits, precisión de ~15 dígitos)
        
    - `decimal` (128 bits, más preciso para cálculos financieros)
        
- **Booleano**:
    
    - `bool` (true o false)
        
- **Caracteres**:
    
    - `char` (16 bits, representa un solo carácter Unicode)
### **2. Tipos de datos por referencia (Reference Types)**

Almacenan direcciones en memoria en lugar de valores reales.

- **Cadenas de texto**:
    
    - `string` (Cadena de caracteres inmutable)
        
- **Objetos**:
    
    - `object` (Tipo base de todos los datos en C#)
        
- **Arreglos**:
    
    - `int[]` (Arreglo de enteros)
        
    - `string[]` (Arreglo de cadenas)
        

### **3. Tipos de datos definidos por el usuario**

C# permite crear nuevos tipos basados en los primitivos y por referencia.
**Enumeraciones (**`enum`**)**: Las enumeraciones son útiles cuando necesitas representar un conjunto fijo de valores. Son ideales para estados, días de la semana, colores, etc.
```c#
enum DiasSemana { Lunes, Martes, Miércoles, Jueves, Viernes, Sábado, Domingo }
DiasSemana hoy = DiasSemana.Jueves;
Console.WriteLine("Hoy es " + hoy);
```
**Estructuras (**`struct`**)**: Las estructuras son similares a las clases, pero se almacenan directamente en la **Stack Memory** y no requieren instancias como los objetos de referencia. Son útiles para tipos pequeños que no necesitan herencia.
```c#
struct Punto {
    public int X;
    public int Y;
}
```
**Clases (**`class`**)**: Las clases son estructuras más avanzadas que permiten crear objetos con atributos y métodos.
```c#
class Persona {
    public string Nombre;
    public int Edad;
}
```
### **4. Tipos dinámicos**

- `dynamic` El tipo `dynamic` en C# permite que el **tipo de una variable se determine en tiempo de ejecución**, en lugar de en tiempo de compilación. Esto significa que puede almacenar cualquier tipo de dato sin una declaración explícita.    
```c#
dynamic dato = "Hola";
Console.WriteLine(dato); // Muestra "Hola"

dato = 123; // Ahora la variable contiene un número
Console.WriteLine(dato + 10); // Muestra 133
```
### **5. Tipos nulos y especiales**

- `nullable` (`int?`, `bool?` → Puede almacenar `null`)
    
- `var` (Inferencia de tipos en compilación)