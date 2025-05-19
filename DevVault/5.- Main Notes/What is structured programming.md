2025-05-17 10:51

status: ==**Completo==

tags:[paradigmas, java, c#, estructurada]

---
# Structured programming
La programación estructurada como el nombre lo dice, es un paradigma que va siguiendo un orden de ejecución, es cuando escribimos un código sigue un ==flujo de ejecución de arriba a abajo ⬇. ==

Viene siendo cualquier bloque de código que siga un orden de ejecución que sigue el orden de arriba a abajo. (**Funciones/Métodos, Bucles, Condicionales**)

---
# EXAMPLE
```java
// Ejemplo de programación estructurada en Java

import java.util.Scanner;

public class ProgramacionEstructurada {
    
    // 1. Estructura Secuencial: método principal que sigue un flujo lógico
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in); // Crear objeto Scanner para leer la entrada del usuario
        
        System.out.println("Bienvenido al programa de suma de números."); // Mensaje inicial
        
        // 2. Estructura de Decisión (Condicional)
        System.out.print("Ingrese el primer número: ");
        double num1 = scanner.nextDouble();
        
        System.out.print("Ingrese el segundo número: ");
        double num2 = scanner.nextDouble();

        if (num1 >= 0 && num2 >= 0) { // Verificación de entrada válida
            double resultado = sumar(num1, num2); // Llamar a la función de suma
            System.out.println("La suma de " + num1 + " y " + num2 + " es " + resultado);
        } else {
            System.out.println("Por favor, ingrese números positivos."); // Mensaje si la validación falla
        }

        // 3. Estructura Iterativa (Bucle)
        System.out.println("\nEjemplo de estructura repetitiva:");
        for (int i = 1; i <= 5; i++) { // Bucle que se ejecuta 5 veces
            System.out.println("Iteración número " + i);
        }

        System.out.println("\nFin del programa."); // Indicación de cierre
        scanner.close(); // Cerrar el Scanner
    }
    
    // Función para realizar la suma (estructura modular)
    public static double sumar(double a, double b) {
        return a + b;
    }
}