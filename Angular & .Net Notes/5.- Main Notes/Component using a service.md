2025-05-25 19:31

tags:[angular],[component],[service]

---
# Component using a service
## 🧠 Uso de un Service en un Componente
### 🎯 Objetivo

Consumir el `UsuarioService` desde un componente para:
- Obtener usuarios (GET)
- Crear un usuario (POST)
- Actualizar un usuario (PUT)
- Eliminar un usuario (DELETE)
### ✅ Flujo resumido
1. `ngOnInit()` carga los usuarios al iniciar.
2. Cada botón llama al método correspondiente del servicio.
3. Se actualiza la lista después de cada acción.
[[#Example Component]]

### 💡 Observable & Subscribe
[[Observable]]

---
# Example
## Example Component
```ts
// src/app/components/usuarios/usuarios.component.ts

import { Component, OnInit } from '@angular/core';
import { UsuarioService } from 'src/app/services/usuario.service';
import { Usuario } from 'src/app/interfaces/usuario';

@Component({
  selector: 'app-usuarios',
  templateUrl: './usuarios.component.html',
})
export class UsuariosComponent implements OnInit {
  usuarios: Usuario[] = [];

  constructor(private usuarioService: UsuarioService) {}

  ngOnInit(): void {
    this.obtenerUsuarios();
  }

  // ✅ GET
  obtenerUsuarios(): void {
    this.usuarioService.getUsuarios().subscribe({
      next: (data) => (this.usuarios = data),
      error: (err) => console.error('Error al obtener usuarios', err)
    });
  }

  // ✅ POST
  crearUsuario(): void {
    const nuevoUsuario: Usuario = {
      id: 0,
      nombre: 'Nuevo Usuario',
      email: 'nuevo@email.com',
      activo: true
    };

    this.usuarioService.crearUsuario(nuevoUsuario).subscribe({
      next: () => this.obtenerUsuarios(),
      error: (err) => console.error('Error al crear usuario', err)
    });
  }

  // ✅ PUT
  actualizarUsuario(usuario: Usuario): void {
    usuario.nombre = 'Nombre Actualizado';
    this.usuarioService.actualizarUsuario(usuario.id, usuario).subscribe({
      next: () => this.obtenerUsuarios(),
      error: (err) => console.error('Error al actualizar usuario', err)
    });
  }

  // ✅ DELETE
  eliminarUsuario(id: number): void {
    this.usuarioService.eliminarUsuario(id).subscribe({
      next: () => this.obtenerUsuarios(),
      error: (err) => console.error('Error al eliminar usuario', err)
    });
  }
}
```

```HTML
<h2>Lista de usuarios</h2>
<ul>
  <li *ngFor="let usuario of usuarios">
    {{ usuario.nombre }} - {{ usuario.email }}
    <button (click)="actualizarUsuario(usuario)">Editar</button>
    <button (click)="eliminarUsuario(usuario.id)">Eliminar</button>
  </li>
</ul>

<button (click)="crearUsuario()">Crear nuevo usuario</button>
```

---
# References
