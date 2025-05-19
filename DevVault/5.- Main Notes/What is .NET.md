2025-05-17 15:44

status: ==**Completo**==

tags: [c#, .NET]

---
# ¿Qué es .NET?
**.NET** es una **plataforma de desarrollo** creada por **Microsoft** que permite construir y ejecutar aplicaciones de distintos tipos:  
- Aplicaciones web
- Aplicaciones de escritorio
- Aplicaciones móviles
- Servicios backend
- APIs REST
- Aplicaciones de consola
- Juegos (con Unity)

.NET es **multiplataforma**, lo que significa que puedes desarrollar para **Windows, Linux y macOS**.

> Actualmente, el nombre oficial de la versión moderna es **.NET** (antes .NET Core), mientras que **.NET Framework** es la versión clásica que solo funciona en Windows.

---
## Componentes clave

- **CLR (Common Language Runtime)**  
  Máquina virtual que ejecuta aplicaciones .NET. Administra memoria, seguridad, ejecución, hilos, excepciones, etc.

- **BCL (Base Class Library)**  
  Conjunto de clases base que proporciona funcionalidad común: cadenas, colecciones, IO, fechas, LINQ, etc.

- **Lenguajes soportados**  
  - C#
  - F#
  - Visual Basic  
  (Todos compilan a un lenguaje intermedio llamado **CIL**)

- **SDK y CLI**  
  El SDK incluye herramientas y bibliotecas necesarias para desarrollar, compilar y ejecutar aplicaciones.  
  La CLI (`dotnet`) permite compilar, correr, testear, crear proyectos desde la terminal.
---
## Historia rápida

| Versión       | Año      | Notas destacadas                    |
|---------------|----------|-------------------------------------|
| .NET Framework 1.0 | 2002     | Solo Windows                      |
| .NET Core 1.0     | 2016     | Multiplataforma, más ligero       |
| .NET 5           | 2020     | Unificación de Core y Framework   |
| .NET 6 LTS       | 2021     | Estable y ampliamente adoptado    |
| .NET 7           | 2022     | Mejora de rendimiento              |
| .NET 8 LTS       | 2023     | Última versión con soporte largo  |

---
## .NET Runtime vs SDK

| Componente | Función                                                                 |
|------------|-------------------------------------------------------------------------|
| SDK        | Herramientas para desarrollo (compilador, CLI, templates, etc.)         |
| Runtime    | Solo lo necesario para ejecutar apps ya compiladas                      |

---
## Características de .NET
- 🧠 **Orientado a objetos**
- ⚙️ **Multiplataforma**
- 🔐 **Seguro y administrado**
- 🔁 **Multilenguaje (C#, F#, VB)**
- 🚀 **Rendimiento alto**
- 🧰 **Gran ecosistema de librerías y herramientas**
- 📦 **NuGet**: gestor de paquetes
---
## ¿Qué puedo construir con .NET?

- **ASP.NET Core** → aplicaciones web modernas, APIs REST
- **Blazor** → apps web interactivas con C# en el navegador
- **MAUI** → apps móviles y de escritorio multiplataforma
- **WPF / WinForms** → apps de escritorio para Windows
- **Unity** → desarrollo de videojuegos con C#
- **Azure Functions** → apps sin servidor (serverless)
- **Aplicaciones de consola** → herramientas, scripts
---
## Diferencia entre .NET y .NET Framework

| Aspecto           | .NET Framework     | .NET (Core y moderno)         |
|-------------------|--------------------|-------------------------------|
| Plataforma         | Solo Windows       | Multiplataforma (Win, Linux…) |
| Abierto            | No                 | Sí (open source)              |
| Rendimiento        | Menor              | Mayor                         |
| Mantenimiento      | Legacy             | Activo                        |
| Modularidad        | Monolítico         | Modular con paquetes NuGet    |

---
## CLI básica (dotnet)

```bash
dotnet new console -n MiApp        # Crear nueva app de consola
dotnet build                       # Compilar
dotnet run                         # Ejecutar
dotnet add package Newtonsoft.Json # Agregar paquete NuGet
dotnet test                        # Ejecutar pruebas
```
---
# Example
```c#
using System;

namespace MiApp {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("Hola desde .NET");
        }
    }
}
```

---
# References
- [https://dotnet.microsoft.com/](https://dotnet.microsoft.com/)
- [Documentación oficial de .NET](https://learn.microsoft.com/es-es/dotnet/)
- [What is .NET? - Microsoft](https://learn.microsoft.com/en-us/dotnet/standard/)