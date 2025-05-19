2025-05-17 17:39

status: ==**Completo**==

tags: [service, backend, mvc, arquitectura, java, c#, spring, aspnet]

---
# ¿Qué es un Servicio (Service)?

Un **Servicio** es una clase cuya responsabilidad principal es **contener la lógica del negocio** de una aplicación.  
Opera como una **capa intermedia entre el controlador y el repositorio** (o cualquier otra fuente de datos), **procesando datos, aplicando reglas y coordinando acciones**.

> El controlador delega al servicio, y el servicio se encarga de ejecutar lo que realmente debe suceder en el sistema.

---
## 🎯 Responsabilidades de un Servicio

- Aplicar **reglas del negocio**.
- Coordinar llamadas a repositorios, validaciones, otros servicios.
- Procesar datos antes de devolverlos al controlador.
- Orquestar operaciones más complejas como transacciones o llamadas múltiples.

---
## 🧩 ¿Qué no debe hacer?

- No debe manejar directamente la petición HTTP (eso es del controlador).
- No debe interactuar directamente con la base de datos (eso es del repositorio).
- No debe tener lógica de presentación.

---
## 🧠 ¿Por qué usar servicios?

- **Separación de responsabilidades**: cada capa tiene su función clara.
- Facilita **las pruebas unitarias**.
- Permite **reutilizar lógica** entre controladores o incluso proyectos.
- Mejora la **escalabilidad** y el mantenimiento del sistema.

---
## 🔗 Relación entre capas

[Controlador]  
↓  
[Servicio] ←→ [Repositorio]

- El **controlador** se encarga de la petición/respuesta.
- El **servicio** de la lógica del negocio.
- El **repositorio** de la persistencia de datos.

---
## 🧰 Buenas prácticas

- Inyectar servicios vía **constructor (inyección de dependencias)**.
- Usar nombres claros como `UsuarioService`, `ProductoService`.
- Mantener los servicios **enfocados en una funcionalidad concreta**.
- No mezclar lógica de infraestructura con lógica del dominio.

---
# Example
```java
@Service
public class ProductService {

    private final ProductRepository productRepo;

    public ProductService(ProductRepository productoRepo) {
        this.productRepo = productRepo;
    }

    public List<Product> GetAll() {
        return productRepo.findAll();
    }

    public Product create(Product product) {
        return productRepo.save(product);
    }
}```

```c#
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
```

---
# References
- [Spring Boot - Business Services](https://docs.spring.io/spring-framework/docs/current/reference/html/business-tier.html)
- [ASP.NET Core Services & Dependency Injection](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection)