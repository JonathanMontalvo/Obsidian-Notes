2025-05-17 12:19

status: ==**Completo**==

tags:[c#, lists, arrays]

---
# Obtener la longitud de listas, arreglos y arreglos bidimensionales

| Propiedad/Método        | Tipo de colección                    | Descripción                                                                    |
| ----------------------- | ------------------------------------ | ------------------------------------------------------------------------------ |
| `.Length`               | Arreglos (`int[]`, `string[]`, etc.) | Devuelve el número total de elementos en el arreglo.                           |
| `.Count`                | Listas (`List<T>`), `IEnumerable<T>` | Devuelve la cantidad de elementos en la colección.                             |
| `.GetLength(dimension)` | Arreglos multidimensionales (`[,]`)  | Devuelve el número de elementos en la dimensión especificada (fila o columna). |

---
# Example
```c#
// Arreglo unidimensional
int[] arreglo = { 1, 2, 3, 4 };
Console.WriteLine(arreglo.Length);  // Output: 4

// Lista genérica
List<string> lista = new List<string> { "a", "b", "c" };
Console.WriteLine(lista.Count);     // Output: 3

// Arreglo bidimensional
int[,] matriz = {
    { 1, 2, 3 },
    { 4, 5, 6 }
};
Console.WriteLine(matriz.Length);          // Output: 6 (total de elementos)
Console.WriteLine(matriz.GetLength(0));    // Output: 2 (filas)
Console.WriteLine(matriz.GetLength(1));    // Output: 3 (columnas)
```

---
# References
