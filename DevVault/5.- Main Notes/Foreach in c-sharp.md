2025-05-17 13:02

status: ==**Completo**==

tags:[c#, iteration]

---
# Foreach
La sentencia `foreach` en C# permite **iterar** fácilmente sobre los elementos de una colección que implemente `IEnumerable` (como listas, arreglos, etc.)
En cada iteración, la variable `elemento` toma el valor de uno de los elementos de la colección. No es necesario llevar índices manuales. Al terminar la colección, el bucle finaliza automáticamente. `foreach` es de solo lectura: no podemos cambiar la colección durante la iteración (no añadir/quitar elementos dentro del bucle). Si la colección está vacía, el cuerpo del `foreach` no se ejecuta

---
# Example
```c#
using System;
using System.Collections.Generic;

class ProgramaForeach {
    static void Main() {
        List<string> nombres = new List<string> { "ana", "juan", "marta" };
        
        // Recorrer la lista con foreach
        foreach (string nombre in nombres) {
            // Mostrar cada nombre convertido a mayúsculas
            Console.WriteLine(nombre.ToUpper());
        }
        // Output:
        // ANA
        // JUAN
        // MARTA
    }
}
```

---
# References
[learn.microsoft.com](https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/statements/iteration-statements#:~:text=La%20instrucci%C3%B3n%20,muestra%20en%20el%20siguiente%20ejemplo)