2025-05-17 17:39

status: ==**Completo**==

tags: [repository, backend, mvc, arquitectura, java, spring, c#, aspnet, datos]

---
# ¿Qué es un Repositorio?

Un **Repositorio** es una **clase o interfaz que encapsula el acceso a los datos** de una aplicación, permitiendo consultar, insertar, actualizar y eliminar información sin exponer los detalles de la base de datos.

Se trata de una **abstracción de la capa de persistencia**, lo que permite que el resto del sistema no tenga que preocuparse por cómo se almacenan o recuperan los datos.

---
## 🧩 ¿Qué hace un Repositorio?

- Proporciona una API limpia para acceder a la base de datos.
- Se comunica con ORM como **JPA/Hibernate** (Java) o **Entity Framework** (C#).
- Aísla al resto del sistema de los detalles de la base de datos.

---
## 🎯 Ventajas de usar repositorios

- **Separación de responsabilidades**: el servicio no accede directamente a la base de datos.
- Facilita el **cambio de tecnología de almacenamiento** sin cambiar la lógica de negocio.
- Permite **mockear datos** fácilmente en pruebas.
- Mejora el **mantenimiento y escalabilidad**.

---
## 📌 ¿Qué no debe hacer un repositorio?

- No debe contener lógica de negocio.
- No debe interactuar con el controlador directamente.
- No debe manejar formato de respuesta ni validaciones.

---
## 🧠 Buenas prácticas

- Usar interfaces como contrato (`IUsuarioRepository`).
- Usar nombres descriptivos: `ProductoRepository`, `UsuarioRepository`.
- Evitar lógica compleja en los repositorios: delegarla a los servicios.

---
## 🔗 Relación con otras capas

[Controlador]  
↓  
[Servicio]  
↓  
[Repositorio]  
↓  
[Base de Datos]

---
## 🧠 Anotaciones relevantes

|Lenguaje|Anotación / Clase|Función|
|---|---|---|
|Java|`@Repository`|Marca clase como repositorio|
|Java|`JpaRepository`|Interfaz con métodos CRUD|
|C#|`DbContext`|Clase que representa la base|
|C#|`IProductoRepository`|Contrato para la implementación|

---
## ✅ Conclusión

Los **repositorios** son esenciales en aplicaciones bien estructuradas.  
Ayudan a mantener una arquitectura limpia y desacoplada, facilitando el mantenimiento y escalabilidad de sistemas complejos.

---
# Example
```java
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {
    List<Product> findByCategory(String category);
    List<Product> findByPriceGreaterThan(double price);
}
```
Con `JpaRepository`, ya tienes métodos como `findAll()`, `save()`, `findById()` listos para usar. Puedes definir métodos personalizados por nombre.

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
```
`AppDbContext` representa el contexto de la base de datos configurado con Entity Framework.

---
# References
- [Spring Data JPA - Repositories](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)
- [Microsoft Docs - Repositories in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/repository-pattern)