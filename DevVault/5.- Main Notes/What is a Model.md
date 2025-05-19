2025-05-17 18:00

status: ==**Completo**==

tags: [modelo, mvc, backend, entidad, spring, aspnet, arquitectura]

---
# ¿Qué es un Modelo (Model)?

En el contexto de desarrollo de software (especialmente en el patrón **MVC**), un **modelo** representa los **datos y la lógica del dominio** del sistema.

> El modelo se encarga de **definir la estructura de los datos** y, en algunos casos, contiene **validaciones o reglas** básicas del dominio.

---
## 🧩 ¿Qué hace un Modelo?

- Representa una **entidad** del mundo real (ej: Usuario, Producto, Pedido).
- Define los **atributos** (campos) que se almacenan.
- En sistemas con ORM, se **mapea** directamente a una tabla en la base de datos.
- Puede incluir **validaciones**, pero no debe contener lógica de negocio compleja (eso es tarea del servicio).

---
## 🎯 ¿Dónde se usa?

- En la capa de **persistencia** (entidades que se guardan en BD).
- En la capa de **negocio** (cuando no se persiste, pero se requiere lógica interna).
- En el **intercambio de datos** (DTOs o ViewModels en algunos casos).

---
## 📌 Tipos de modelos

| Tipo                       | Propósito principal                          |
| -------------------------- | -------------------------------------------- |
| Modelo de dominio          | Representa entidades reales del negocio      |
| DTO (Data Transfer Object) | Optimiza los datos que viajan entre capas    |
| ViewModel                  | Estructura pensada para la vista (front-end) |

---
## ✅ Buenas prácticas

- Mantenlos **simples y enfocados** en representar datos.
- Si usas DTOs, **no mezcles entidades con datos de presentación**.
- Usa anotaciones como `@Entity`, `@Id` en Java, y `DataAnnotations` en C# para validaciones o mapeo.

---
## 🧠 Relación en MVC

[Vista] ←→ [Controlador] ←→ [Servicio] ←→ [Modelo] ←→ [Repositorio]
El **modelo** es el corazón de los datos del sistema.

---
# Example
```java
@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private double price;

    public Product() {}

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    // Getters y Setters
    public Long getId() { return id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public double getPrice() { return price; }
    public void setPrice(double price) { this.price = price; }
}
```

```c#
public class Product {
    public int Id { get; set; }
    public string Name { get; set; }
    public double Price { get; set; }

    public Product() {}

    public Product(string name, double price) {
        Name = name;
        Price = price;
    }
}
```

> En ambos casos, estos modelos pueden ser utilizados por los repositorios para ser persistidos en la base de datos, o bien pasados entre controladores y servicios.

---
# References
- [Spring JPA Entity Basics](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.entities)
- [Microsoft Docs - Models in ASP.NET Core MVC](https://learn.microsoft.com/en-us/aspnet/core/mvc/models)