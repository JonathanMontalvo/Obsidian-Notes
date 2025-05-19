2025-05-17 17:38

status: ==**Completo**==

tags: [backend, json, datos, formato, api, serializacion, interoperabilidad]

---
# ¿Qué es JSON?

**JSON (JavaScript Object Notation)** es un **formato ligero de intercambio de datos**, fácil de leer y escribir tanto para humanos como para máquinas.

Se utiliza ampliamente para comunicar información entre un cliente (por ejemplo, navegador) y un servidor (por ejemplo, API REST).

> Aunque deriva de la sintaxis de objetos de JavaScript, **es independiente del lenguaje** y es compatible con prácticamente todos los lenguajes modernos.

---
## 📦 ¿Para qué se usa?

- Transmitir datos en aplicaciones web (API REST).
- Guardar configuraciones o archivos de datos (ej. `config.json`).
- Serializar y deserializar objetos (convertir objetos a texto y viceversa).

---
## ✍️ Sintaxis básica

Un JSON está compuesto por:

- **Objetos**: Delimitados por `{ }`, contienen pares `clave: valor`.
- **Arreglos**: Delimitados por `[ ]`, contienen listas ordenadas de elementos.
- **Valores**: `string`, `number`, `boolean`, `null`, objeto o arreglo.

---
## 🧠 Reglas clave

- Las claves deben ir entre **comillas dobles** `"clave"`.
- Los valores pueden ser de diferentes tipos.
- No se permiten **comentarios** en JSON estándar.
- Usa **UTF-8** por defecto.

---
## ✅ Ventajas

- Legible y simple.
- Compatible con muchos lenguajes.
- Ideal para estructuras jerárquicas.
- Muy usado en APIs y sistemas distribuidos.

---
## ❗ Desventajas
- No soporta comentarios (como YAML).
- No maneja tipos complejos nativos como fechas (requiere transformación).
- Más verboso que otros formatos como MessagePack o Protocol Buffers.

---
## 🧪 Herramientas útiles

- [jsonlint.com](https://jsonlint.com) – Validar sintaxis.
- Extensiones de VS Code como **JSON Formatter** o **Prettier**.
- Postman – para probar APIs que devuelven/reciben JSON.

---
# Example
```json
{
  "nombre": "Jonathan",
  "edad": 23,
  "activo": true,
  "lenguajes": ["Java", "C#", "JavaScript"],
  "direccion": {
    "ciudad": "Toluca",
    "pais": "México"
  },
  "notas": null
}```

## 🔁 Serialización y deserialización

### En Java (Jackson):
```java
ObjectMapper mapper = new ObjectMapper();

// De objeto a JSON
String json = mapper.writeValueAsString(objeto);

// De JSON a objeto
MiClase obj = mapper.readValue(json, MiClase.class);
```
### En C# (.NET):
```c#
using System.Text.Json;

// De objeto a JSON
string json = JsonSerializer.Serialize(objeto);

// De JSON a objeto
var obj = JsonSerializer.Deserialize<MiClase>(json);
```
---
# References
- [json.org](https://www.json.org/json-es.html)
- [Wikipedia - JSON](https://es.wikipedia.org/wiki/JSON)
- [Microsoft Docs - JSON in .NET](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-overview)
- [Jackson (Java)](https://github.com/FasterXML/jackson)