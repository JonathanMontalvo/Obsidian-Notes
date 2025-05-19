2025-05-17 14:02

status: ==**Completo**==

tags:[paradigmas, c#, oop]

---
# Namespace
Un **`namespace`** en C# es un **contenedor lógico** que permite **organizar y agrupar** los distintos elementos del código como:
- Clases
- Interfaces
- Enumeraciones
- Estructuras
- Delegados

Su principal propósito es:
- **Evitar conflictos de nombres** cuando diferentes bibliotecas o módulos tienen clases con nombres iguales.
- **Facilitar la lectura y el mantenimiento** de proyectos medianos o grandes al dividir el código en módulos bien definidos.

> Los `namespace` no alteran el funcionamiento del programa, pero son cruciales para estructurarlo correctamente.

---
## ¿Cómo se usan?

Para acceder a un tipo que está definido dentro de un `namespace`, hay dos formas principales:

1. **Mediante la palabra clave `using`**:
   Permite importar el espacio de nombres para poder usar sus clases sin necesidad de escribir el nombre completo.

2. **Usando el nombre completamente calificado**:
   Especificas el `namespace` cada vez que haces referencia a una clase.

---
## Recomendaciones de uso

- Usa `namespace` para agrupar clases relacionadas por funcionalidad.
- No crees un solo `namespace` para todo el proyecto.
- Usa nombres jerárquicos que reflejen la estructura del proyecto:  
  Ejemplo: `MiApp.Modelos`, `MiApp.Servicios`, `MiApp.Controles`.

---
## Namespace anidados

Un `namespace` puede contener otros `namespace`, lo cual permite una **organización jerárquica** del código.  
Esto es útil cuando tienes módulos grandes que necesitan submódulos internos.

---
## Namespace global

A partir de **C# 10**, se introdujo el concepto de **`global using`**, que permite importar espacios de nombres de forma **global** para todo el proyecto. Esto es útil para evitar repetir muchos `using` en cada archivo.
- Se recomienda colocar estos `global using` en un archivo especial llamado, por convención, `_Imports.cs` o `Usings.cs` en la raíz del proyecto.
- Esta funcionalidad es especialmente útil en aplicaciones grandes o con muchos archivos.

---
## Ventajas de usar namespaces:
- **Evitan colisiones de nombres** entre clases con el mismo nombre en distintos contextos.
- **Organizan** el código en módulos o capas (por ejemplo: `Proyecto.Modelos`, `Proyecto.Servicios`).
- Facilitan el uso de librerías externas sin conflicto.
---
# Example
## Namespace básico

```c#
namespace Utilidades {
    public class Conversor {
        public static double CelsiusAFahrenheit(double c) {
            return c * 9 / 5 + 32;
        }
    }
}
```
## Namespace  con `using`
```c#
using Utilidades;

class Programa {
    static void Main() {
        double f = Conversor.CelsiusAFahrenheit(30);
        Console.WriteLine($"Temperatura en Fahrenheit: {f}");
    }
}

```
## Namespace anidado
```c#
namespace MiApp.Servicios {
    namespace Seguridad {
        public class Encriptador {
            public static string Encriptar(string texto) {
                return $"##{texto}##"; // Simulación
            }
        }
    }
}

using MiApp.Servicios.Seguridad;
class Programa {
    static void Main() {
        string r = Encriptador.Encriptar("clave");
        Console.WriteLine(r); // ##clave##
    }
}
```
## Global using (desde C# 10)
```c#
global using System.Text;
StringBuilder sb = new StringBuilder();
sb.Append("Hola mundo");
Console.WriteLine(sb.ToString());
```
---
# References
- [Namespaces en C# - Microsoft Docs](https://learn.microsoft.com/es-es/dotnet/csharp/fundamentals/types/namespaces)