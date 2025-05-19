2025-05-17 17:29

status: ==**Completo**==

tags: [controller, mvc, java, c#, backend, arquitectura, desarrollo web, api, base de datos, servidor]

---
# ¿Qué es un Controller?

Un **Controller** (Controlador) es un **componente clave en el patrón de arquitectura MVC** (Model-View-Controller) que actúa como **intermediario entre el cliente (por ejemplo, el frontend) y el backend**.

Su función principal es:
- **Recibir peticiones HTTP** (GET, POST, PUT, DELETE, etc.).
- **Delegar la lógica al servicio correspondiente**.
- **Devolver una respuesta** al cliente (por ejemplo, en formato JSON).

---
## 📌 ¿Dónde se usa un Controller?

- En aplicaciones **web y API REST** construidas con frameworks como **Spring Boot** o **ASP.NET Core**.
- Es un punto de entrada donde las rutas (URLs) se mapean a métodos que ejecutan acciones específicas.

---
## 🧩 ¿Qué hace un Controller?

1. **Mapea rutas**: vincula URLs a funciones.
2. **Recibe parámetros**: desde la URL, el cuerpo de la petición o la cabecera.
3. **Valida datos** (en algunos casos).
4. **Llama a los servicios** que contienen la lógica del negocio.
5. **Retorna una respuesta** al cliente (HTML, JSON, XML, etc.).

---
## ⚙️ ¿Qué no hace?

===Un controlador **NO debe tener la lógica del negocio**, esa debe estar en una capa de servicios.  
Su rol es de **orquestación y enrutamiento**.==

---
## 🎯 Buenas prácticas

- Mantener los controladores **delgados y simples**.
- Delegar procesamiento a servicios o casos de uso.
- Usar anotaciones claras y manejar los errores de forma controlada.
- Separar los controladores por dominio (ej. `UserController`, `ProductController`).

---
## 🧠 Anotaciones importantes

|Lenguaje|Anotación|Función|
|---|---|---|
|Java|`@RestController`|Declara que es un controller REST|
|Java|`@RequestMapping`|Define la ruta base|
|Java|`@GetMapping`, `@PostMapping`|Mapeo de métodos HTTP|
|C#|`[ApiController]`|Marca clase como controlador REST|
|C#|`[Route("api/[controller]")]`|Ruta base del controlador|
|C#|`[HttpGet]`, `[HttpPost]`|Define métodos HTTP|

---
## 🧭 Relación con otras capas

[Cliente (Frontend)]
         ↓
[Controller] ←→ [Servicios / Use Cases] ←→ [Repositorio / DB]

El **controller** solo debe recibir peticiones, extraer datos, delegar, y retornar resultados.

---
# Example
```java
@RestController
@RequestMapping("/api/productos")
public class ProductController {

    private final ProductService productService;

    public ProductController(ProductService productService) {
        this.productService = productService;
    }

    @GetMapping
    public List<Product> GetProducts() {
        return productService.GetAll();
    }

    @PostMapping
    public Product createProduct(@RequestBody Product product) {
        return productService.create(product);
    }
}
```

```c#
[ApiController]
[Route("api/[controller]")]
public class ProductController : ControllerBase
{
    private readonly IProductService _productService;

    public ProductController(IProductService productService)
    {
        _productService = productService;
    }

    [HttpGet]
    public IActionResult GetProducts()
    {
        var products = _productService.GetAll();
        return Ok(products);
    }

    [HttpPost]
    public IActionResult CreateProduct([FromBody] Product product)
    {
        var newProduct = _productService.Create(product);
        return CreatedAtAction(nameof(GetProducts), new { id = newProduct.Id }, newProduct);
    }
}
```
---
# References
- [Spring Boot Controllers - Docs](https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#mvc-controller)
- [ASP.NET Controllers - Microsoft Docs](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/)