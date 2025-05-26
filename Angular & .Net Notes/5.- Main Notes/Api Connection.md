2025-05-25 18:38

tags: [angular], [API]

---
# Api Connection
## 🌐 Conexión con una API
### 📁 ¿Qué contiene la carpeta `environments/`?
Esta carpeta contiene archivos de configuración por entorno:
```cpp
src/
├── environments/
│   ├── environment.ts          // Configuración para desarrollo (default)
│   └── environment.prod.ts     // Configuración para producción
```
### 🧠 ¿Para qué sirve?
Para definir variables distintas según el entorno (desarrollo o producción). Ejemplo:
```ts
// environment.ts
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000/api'
};
```
```ts
// environment.prod.ts
export const environment = {
  production: true,
  apiUrl: 'https://mi-api-en-produccion.com/api'
};
```
[[#Example]]

---
# Example
### ✅ Cómo usarlo en tu app
```ts
import { environment } from 'src/environments/environment';
console.log(environment.apiUrl);
```