2025-05-17 18:13

status: ==**Completo**==

tags: [backend, inyeccion-dependencias, spring, aspnet, arquitectura, id, inversion-control]

---
# ¿Qué es la Inyección de Dependencias (ID)?

La **Inyección de Dependencias (Dependency Injection)** es un **patrón de diseño** que permite que un objeto reciba ("le inyecten") las dependencias que necesita para funcionar, en lugar de crearlas por sí mismo.

> Se basa en el principio de **Inversión de Control (IoC)**, donde la creación y gestión de los objetos se delega a un **contenedor o framework**.

---
## 🎯 ¿Para qué sirve?

- **Desacopla componentes**: los objetos no necesitan saber cómo se crean sus dependencias.
- **Facilita pruebas** (por ejemplo, usando mocks).
- **Mejora la mantenibilidad** y la legibilidad del código.
- Favorece la **inyección de distintos comportamientos** (polimorfismo e interfaces).

---
## 📦 ¿Qué es una dependencia?

Una dependencia es **cualquier objeto que otra clase necesita** para trabajar.  
Ejemplo: un `ServicioProducto` depende de un `RepositorioProducto` para acceder a los datos.

---
## 🔄 Tipos comunes de inyección

| Tipo          | Descripción                                                  |
|---------------|--------------------------------------------------------------|
| Constructor   | Se inyectan dependencias a través del constructor.           |
| Setter        | Se inyectan a través de métodos `set`.                       |
| Por campo     | El framework inyecta directamente en el atributo (Java).     |

---
## ✅ Buenas prácticas

- Inyecta dependencias a través del **constructor**: es más seguro y claro.
- Inyecta **interfaces**, no implementaciones.
- Evita la creación manual de dependencias (`new`) dentro de los controladores o servicios.
- No abuses de la inyección directa por atributo (en Java), pierde claridad en pruebas y refactorizaciones.

---
## 💡 Analogía rápida

Imagina que una **cafetera (servicio)** necesita **agua (dependencia)**.  
Con ID, **no tiene que ir a buscarla**, se la entregan directamente.

---
## 🧠 Relación entre capas

[Controller] ---> [Servicio] ---> [Repositorio]
				 ↑
		   Inyección de dependencias

---
# Example
```java
@Service
public class ProductoService {

    private final ProductoRepository productoRepository;

    // Inyección por constructor
    @Autowired
    public ProductoService(ProductoRepository productoRepository) {
        this.productoRepository = productoRepository;
    }

    public List<Producto> listarProductos() {
        return productoRepository.findAll();
    }
}
@Repository
public interface ProductoRepository extends JpaRepository<Producto, Long> {
}
@RestController
@RequestMapping("/productos")
public class ProductoController {

    private final ProductoService productoService;

    @Autowired
    public ProductoController(ProductoService productoService) {
        this.productoService = productoService;
    }

    @GetMapping
    public List<Producto> obtenerProductos() {
        return productoService.listarProductos();
    }
}
```
### 🛠️ Ejemplo en C# (ASP.NET Core)
```c#
public interface IProductRepository {
    IEnumerable<Product> GetAll();
    Producto Create(Product product);
}

public class ProductRepository : IProductRepository {

    private readonly AppDbContext _context;

    public ProductRepository(AppDbContext context) {
        _context = context;
    }

    public IEnumerable<Product> GetAll() {
        return _context.Product.ToList();
    }

    public Product Create(Product product) {
        _context.Product.Add(product);
        _context.SaveChanges();
        return product;
    }
}
public interface IProductService {
    IEnumerable<Product> GetAll();
    Product Create(Product product);
}

public class ProductService : IProductService {

    private readonly IProductRepository _productRepo;

    public ProductService(IProductRepository productRepo) {
        _productRepo = productRepo;
    }

    public IEnumerable<Product> GetAll() {
        return _productRepo.GetAll();
    }

    public Producto Create(Product product) {
        return _productRepo.Create(product);
    }
}
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
### 📌 Registro de dependencias en `Program.cs`
```c#
builder.Services.AddScoped<IProductRepository, ProductRepository>();
builder.Services.AddScoped<IProductService,ProductService>();
```
---
# References
- [Spring Docs - Dependency Injection](https://docs.spring.io/spring-framework/reference/core/beans/dependencies.html)
- [Microsoft Docs - Dependency injection in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection)