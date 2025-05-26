2025-05-25 19:19

tags:[angular], [interface], [service]

---
# Interface y Service
## 📐 Interface (`ng g interface`)
#### ¿Qué es una Interface?

Una **interface** define la forma o estructura de un objeto en TypeScript. Se usa en Angular para **tipar los datos**, especialmente cuando consumes APIs o defines modelos de tus entidades.
```bash
ng generate interface interfaces/usuario
```
Alias:
```bash
ng g i interfaces/usuario
```
#### ¿Dónde se usa?
- En servicios para tipar respuestas HTTP.
- En formularios para crear objetos válidos.
- En componentes para validar props o entradas.
[[#Example Interface]]
---
## 🔧 Service (`ng g service`)
#### ¿Qué es un Service?
Un **service** en Angular contiene lógica que debe ser compartida entre componentes. Se usa comúnmente para:
- Hacer **peticiones HTTP** a APIs.
- Encapsular **reglas de negocio**.
- Compartir **estado o datos** entre componentes.
#### Comando para generar un service:
```bash
ng generate service services/usuario
```
Alias:
```bash
ng g s services/usuario
```
[[#Example Service]]

---
# Example
## Example Interface
```ts
export interface Usuario {
  id: number;
  nombre: string;
  email: string;
  activo: boolean;
}
```

## Example Service
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';
import { Usuario } from '../interfaces/usuario';
import { environment } from 'src/environments/environment';

@Injectable({
  providedIn: 'root'
})
export class UsuarioService {
  private _myAppUrl: string = environment.endpoint;
  private _myApiUrl: string = 'api/Order/';

  constructor(private http: HttpClient) {}

  // ✅ GET - Obtener todos los usuarios
  getUsuarios(): Observable<Usuario[]> {
    return this.http.get<Usuario[]>(`${this._myAppUrl}${this._myApiUrl}`);
  }

  // ✅ GET - Obtener un usuario por ID
  getUsuario(id: number): Observable<Usuario> {
    return this.http.get<Usuario>(`${this._myAppUrl}${this._myApiUrl}${id}`);
  }

  // ✅ POST - Crear nuevo usuario
  crearUsuario(usuario: Usuario): Observable<Usuario> {
    return this.http.post<Usuario>(`${this._myAppUrl}${this._myApiUrl}`, usuario);
  }

  // ✅ PUT - Actualizar usuario existente
  actualizarUsuario(id: number, usuario: Usuario): Observable<Usuario> {
    return this.http.put<Usuario>(`${this._myAppUrl}${this._myApiUrl}${id}`, usuario);
  }

  // ✅ DELETE - Eliminar usuario
  eliminarUsuario(id: number): Observable<void> {
    return this.http.delete<void>(`${this._myAppUrl}${this._myApiUrl}${id}`);
  }
}
```

---
# References
