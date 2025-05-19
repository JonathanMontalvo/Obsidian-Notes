2025-05-17 11:44

status: ==**Completo

tags:

---
#  **📌 ¿Qué es un array en C#?**

Un **array** (arreglo) es una estructura de datos que almacena múltiples valores **del mismo tipo** en una sola variable. Permite acceder a sus elementos a través de **índices**.

📌 **Características de los arrays en C#:** ✅ Pueden ser de **tipo primitivo** (`int`, `float`, `string`, etc.) o **objetos**. ✅ Se acceden mediante **índices**, comenzando desde `0`. ✅ Su tamaño se define en el momento de la creación y **no puede cambiar** después.


---
# Example
## Inicializando tamaño del arreglo y llenando después.

```c#
using System;

class ArrayEjemplo {
    public static void Main() {
        // Declaración de un array de enteros con 5 elementos
        int[] numeros = new int[5];

        // Asignación de valores a los elementos
        numeros[0] = 10;
        numeros[1] = 20;
        numeros[2] = 30;
        numeros[3] = 40;
        numeros[4] = 50;

        // Acceso y recorrido del array
        Console.WriteLine("Elementos del array:");
        for (int i = 0; i < numeros.Length; i++) {
            Console.WriteLine($"Índice {i}: {numeros[i]}");
        }
    }
}
```

## **Inicialización de un array directamente**

En lugar de declarar su tamaño, podemos **inicializar** el array con valores desde el principio:
```c#
string[] colores = { "Rojo", "Verde", "Azul", "Amarillo" };
int[] numeros = new int [5]{1,2,3,4,5};

Console.WriteLine($"Primer color: {colores[0]}");
Console.WriteLine($"Último color: {colores[colores.Length - 1]}"); // Acceder al último elemento
```

## **Array Multidimensional (Matrices)**
```c#
int[,] matriz = {
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};

// Accediendo a un elemento específico
Console.WriteLine($"Elemento en fila 1, columna 2: {matriz[0,1]}"); // Muestra '2'

// Recorriendo la matriz
Console.WriteLine("Elementos de la matriz:");
for (int i = 0; i < matriz.GetLength(0); i++) {
    for (int j = 0; j < matriz.GetLength(1); j++) {
        Console.Write(matriz[i, j] + " ");
    }
    Console.WriteLine();
}
```