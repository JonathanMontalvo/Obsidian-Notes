2025-05-17 18:08

status: ==**Completo**==

tags: [dto, backend, arquitectura, mvc, datos, transferencia]

---
# ¿Qué es un DTO?

Un **DTO (Data Transfer Object)** es un **objeto plano** que se utiliza para **transportar datos** entre distintas capas de una aplicación o a través de una red (por ejemplo, una API REST).

> Sirve como una **representación simplificada de una entidad**, adaptada a las necesidades de comunicación o presentación.

---
## 🎯 ¿Por qué usar DTOs?

- **Separan la lógica de dominio de la exposición de datos** (lo que se muestra al usuario o cliente).
- Permiten **evitar el envío de información sensible** (por ejemplo, contraseñas, tokens).
- Reducen la cantidad de datos transferidos en una petición (mayor eficiencia).
- **Previenen dependencias innecesarias** entre capas (desacoplamiento).
- Pueden tener una estructura distinta a la de la entidad original (ej. incluir datos combinados o derivados).

---
## 🧩 ¿Qué contiene un DTO?

- Atributos **necesarios para un caso específico** (como mostrar, actualizar o crear datos).
- Normalmente **no contiene lógica de negocio**.
- Se usa principalmente en:
  - Peticiones HTTP (body de una API)
  - Respuestas HTTP
  - Comunicación entre capas

---
## ✅ Buenas prácticas

- No reutilices tus **entidades** como DTOs directamente.
- Si necesitas una transformación compleja, considera usar **MapStruct (Java)** o **AutoMapper (C#)**.
- Usa DTOs distintos para lectura (GET) y escritura (POST/PUT) si es necesario.

---
## 🧠 Diferencias con una entidad

|Concepto|Entidad|DTO|
|---|---|---|
|Propósito|Representa datos del dominio|Transporta datos entre capas|
|Estructura|Completa, con relaciones y anotaciones ORM|Simple, solo los datos necesarios|
|Comportamiento|Puede tener lógica de negocio o validaciones complejas|No contiene lógica|
|Mapeo a BD|Sí (con JPA o EF)|No|
|Seguridad|Puede exponer campos sensibles|No debería contener datos sensibles|

---
# Example

```java
// ProductoDTO.java
public class ProductoDTO {

    private String nombre;
    private double precio;

    // Constructor vacío
    public ProductoDTO() {}

    // Constructor con datos
    public ProductoDTO(String nombre, double precio) {
        this.nombre = nombre;
        this.precio = precio;
    }

    // Getters y setters
    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }

    public double getPrecio() { return precio; }
    public void setPrecio(double precio) { this.precio = precio; }
}
//Uso tipico en el controlador
@PostMapping("/productos")
public ResponseEntity<Void> crearProducto(@RequestBody ProductoDTO dto) {
    Producto nuevo = new Producto(dto.getNombre(), dto.getPrecio());
    productoRepository.save(nuevo);
    return ResponseEntity.status(HttpStatus.CREATED).build();
}

```

```c#
// ProductoDTO.cs
public class ProductoDTO
{
    public string Nombre { get; set; }
    public double Precio { get; set; }
}
//Uso en un controlador
[HttpPost]
public IActionResult CrearProducto([FromBody] ProductoDTO dto)
{
    var producto = new Producto
    {
        Nombre = dto.Nombre,
        Precio = dto.Precio
    };

    _context.Productos.Add(producto);
    _context.SaveChanges();

    return CreatedAtAction(nameof(ObtenerProducto), new { id = producto.Id }, producto);
}
```
---
# References
- [Microsoft Docs – DTOs](https://learn.microsoft.com/en-us/aspnet/core/web-api/advanced/formatting)
- [Baeldung – DTO vs Entity](https://www.baeldung.com/entity-to-dto-conversion)