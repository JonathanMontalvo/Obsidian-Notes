2025-05-17 17:24

status: ==**Completo**==

tags: [backend, arquitectura, desarrollo web, api, base de datos, servidor]

---
# ¿Qué es el Backend?

El **Backend** es la parte **no visible** de una aplicación o sistema, que se encarga de la **lógica del negocio**, el **almacenamiento de datos**, la **autenticación**, la **seguridad**, y la **comunicación entre componentes**.  
Todo lo que ocurre “detrás del telón” en una aplicación se considera parte del backend.

> El backend se ejecuta en el **servidor** y responde a peticiones del frontend o de otras aplicaciones.

---
## 🔧 ¿Qué hace el Backend?

- Procesa las **reglas de negocio**.
- Se comunica con **bases de datos**.
- Expone **APIs** para que otros sistemas (o el frontend) consuman información.
- Maneja la **autenticación y autorización**.
- Realiza tareas como validación, encriptación, logs, pagos, colas de procesos, etc.

---
## ⚙️ Componentes del Backend

| Componente             | Función principal                                        |
|------------------------|----------------------------------------------------------|
| Servidor Web           | Recibe las peticiones HTTP y las redirige a la lógica   |
| Lógica del negocio     | Regla del dominio, procesamiento de datos               |
| Base de datos          | Almacenamiento y consulta de datos persistentes         |
| API / Controladores    | Puentes que conectan frontend con el backend            |
| Servicios auxiliares   | Envío de correos, colas, almacenamiento en la nube, etc |

---
## 📡 Comunicación con el Frontend

El backend expone **servicios (APIs)** que pueden ser consumidos por aplicaciones cliente (frontend, móviles, otros servicios).

Ejemplo de flujo:
1. El usuario hace clic en “Ver perfil”.
2. El frontend hace una petición HTTP `GET /api/perfil`.
3. El backend procesa la petición, accede a la base de datos y devuelve una respuesta en JSON.

---
## 🔐 Seguridad y Backend

El backend es responsable de:

- Validar entradas del usuario.
- Gestionar **tokens de autenticación (JWT, OAuth)**.
- Cifrar contraseñas.
- Aplicar reglas de autorización.

---
## 🧰 Tecnologías comunes

| Lenguaje         | Frameworks populares           |
|------------------|--------------------------------|
| **Java**         | Spring Boot                    |
| **C#**           | ASP.NET Core                   |
| **Node.js**      | Express.js, NestJS             |
| **Python**       | Django, Flask                  |
| **PHP**          | Laravel                        |
| **Ruby**         | Ruby on Rails                  |
| **Go**           | Gin, Fiber                     |

---
## 🗃️ Bases de datos utilizadas

| Tipo                  | Ejemplos                              |
|-----------------------|---------------------------------------|
| Relacional (SQL)      | MySQL, PostgreSQL, SQL Server, Oracle |
| No Relacional (NoSQL) | MongoDB, Redis, Firebase, Cassandra   |

---
## 📦 API (Interfaz de Programación de Aplicaciones)

El backend expone sus funcionalidades mediante APIs (REST, GraphQL, gRPC), que permiten la comunicación controlada entre distintos componentes de software.

---
## 🧠 Buenas prácticas

- Separar capas: **controladores, servicios, repositorios**.
- Manejar errores correctamente (códigos HTTP).
- Validar y sanitizar datos de entrada.
- Documentar las APIs (Swagger, Postman).
- Usar arquitecturas limpias y patrones (MVC, DDD, Clean Architecture).

---
## 🆚 Diferencia con el Frontend

| Aspecto      | Frontend                          | Backend                           |
|--------------|-----------------------------------|-----------------------------------|
| Corre en     | Navegador del cliente             | Servidor                          |
| Lenguajes    | HTML, CSS, JavaScript, TypeScript | Java, C#, Python, PHP, etc.       |
| Enfocado en  | Interfaz y experiencia de usuario | Lógica, reglas y datos            |
| Comunicación | Llama a APIs                      | Responde a peticiones             |

---
# Example
```java
@RestController
@RequestMapping("/api/productos")
public class ProductController {
    @GetMapping
    public List<String> getProductos() {
        return Arrays.asList("Product1", "Product2");
    }
}
```

```c#
[ApiController]
[Route("api/[controller]")]
public class ProductController : ControllerBase
{
    [HttpGet]
    public IEnumerable<string> Get()
    {
        return new string[] { "Product1", "Product2" };
    }
}
```
---
# References
- [Microsoft Learn - Backend Overview](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)
- [Spring Boot Docs](https://spring.io/projects/spring-boot)
- [ASP.NET Core Documentation](https://learn.microsoft.com/en-us/aspnet/core/)