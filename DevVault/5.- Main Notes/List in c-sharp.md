2025-05-17 11:17

status: ==**Completo**==

tags:[c#, list]

---
# Introduction to lists in C# #
la clase `List<T>` (espacio de nombres `System.Collections.Generic`) representa una **lista genérica dinámica** de elementos tipados. A diferencia de un array tradicional de tamaño fijo, una `List<T>` puede crecer o reducir su capacidad automáticamente cuando agregamos o quitamos elementos. Internamente mantiene un array que se redimensiona según sea necesario. 

## Métodos comunes de listas
La clase `List<T>` ofrece varios **métodos útiles** para manipular el contenido de la lista. Algunos de los más comunes son:
- `Add(T item)`: agrega un elemento al final de la lista.
- `AddRange(IEnumerable<T> collection)`: agrega todos los elementos de otra colección al final.
- `Remove(T item)`: elimina la primera aparición de un elemento específico y devuelve `true` si lo encontró.
- `RemoveAt(int index)`: quita el elemento en la posición dada.
- `Clear()`: elimina todos los elementos de la lista.
- `Contains(T item)`: indica si la lista contiene el elemento (booleano).
- `IndexOf(T item)`: devuelve el índice de la primera aparición del elemento, o -1 si no existe.
- `Find(Predicate<T> match)`: devuelve el primer elemento que cumpla la condición dada (predicado) o `default(T)` si no hay coincidencia.
- `Sort()`: ordena los elementos de la lista usando el comparador predeterminado o uno personalizado.
- `ForEach(Action<T> action)`: ejecuta una acción (delegado) sobre cada elemento de la lista.

---
# Example#
## Declaración de una lista
Se utiliza la palabra clave **List** seguido del generic que se utilizara para esa lista
```c#
List<T> miLista = new List<T>();
List<string> miListaCadenas = new List<string>();
var miListaNumeros = new List<int>();
```
## Inicialización de una lista con elementos
Esta instrucción crea una lista de cadenas con tres elementos. Podemos acceder a los elementos por índice (`frutas[0]` será `"Manzana"`) y modificarla dinámicamente.
```c#
var frutas = new List<string> { "Manzana", "Naranja", "Banana" };
```
## Uso de una lista
Esta instrucción crea una lista de cadenas con tres elementos. Podemos acceder a los elementos por índice (`frutas[0]` será `"Manzana"`) y modificarla dinámicamente.
```c#
using System;
using System.Collections.Generic;

class ProgramaListas {
    static void Main() {
        // Crear una lista de enteros vacía
        List<int> numeros = new List<int>();

        // Agregar elementos usando Add
        numeros.Add(10);
        numeros.Add(20);
        numeros.Add(30);

        // También podemos inicializar la lista con valores
        List<int> otros = new List<int> { 5, 15 };

        // Mostrar contenido de la lista 'numeros' usando foreach
        Console.WriteLine("Lista 'numeros':");
        foreach (int n in numeros) {
            Console.WriteLine(n);
        }
        // Resultado: 10, 20, 30 (cada uno en una línea)

        // Acceder por índice
        Console.WriteLine($"Primer elemento: {numeros[0]}"); // 10
        // Cambiar un elemento por índice
        numeros[1] = 25; // Cambiamos 20 por 25
        Console.WriteLine($"Segundo elemento modificado: {numeros[1]}"); // 25
    }
}
```
## Métodos comunes de una lista
```c#
using System;
using System.Collections.Generic;

class ProgramaMetodosList {
    static void Main() {
        List<string> frutas = new List<string>();
        
        // Agregar elementos
        frutas.Add("Manzana");
        frutas.Add("Naranja");
        frutas.Add("Plátano");
        Console.WriteLine($"Hay {frutas.Count} frutas en la lista.");

        // Verificar existencia
        if (frutas.Contains("Naranja")) {
            Console.WriteLine("Naranja está en la lista.");
        }

        // Encontrar con Find (por ejemplo, fruta que empiece con 'P')
        string frutaP = frutas.Find(f => f.StartsWith("P"));
        Console.WriteLine($"Fruta que empieza con P: {frutaP}");

        // Eliminar un elemento
        frutas.Remove("Manzana"); // devuelve true si existía
        Console.WriteLine($"Después de Remove, quedan {frutas.Count} frutas.");

        // Ordenar la lista alfabéticamente
        frutas.Sort();
        Console.WriteLine("Frutas ordenadas:");
        foreach (var f in frutas) {
            Console.WriteLine(f);
        }
        //
        Console.WriteLine("Frutas ordenadas:");
    }
}
```