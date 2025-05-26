2025-05-25 18:23

tags:

---
# Create things
## 🚀 Crear nuevo proyecto Angular
```bash
ng new nombre_del_proyecto --standalone=false
```
`--standalone=false` crea el proyecto con módulos clásicos.

---
## ▶️ Ejecutar el proyecto
```bash
ng serve --open
```
Alias:
```
ng s -o
```
---
## 📦 Build del proyecto
```bash
ng build --configuration production --aot
```
> `--aot` activa el Ahead-of-Time compilation para producción.
---
## 🧩 Generar componentes
```bash
ng generate component components/nombre_del_componente
```
Alias
```bash
ng g c components/nombre_del_componente
```
---
## 🛠️ Generar servicios
```bash
ng generate service services/nombre_del_servicio
```
Alias:
```
ng g s services/nombre_del_servicio
```
---
## 📦 Generar módulos (por ejemplo: Shared)
```bash
ng generate module shared/shared
```
Alias:
```bash
ng g m shared/shared
```
---
## 📝 Crear interfaces
```bash
ng generate interface interfaces/nombre_de_interface
```
Alias:
```bash
ng g i interfaces/nombre_de_interface
```
---
## 🔐 Guard (`ng g guard`)

#### ¿Qué es un Guard?

Un **Guard** protege rutas. Se usa para decidir si se puede **activar o desactivar una ruta**, según condiciones como si el usuario está autenticado.
#### Comando para generar un guard:
```bash
ng generate guard guards/auth
```
Alias:
```bash
ng g guard guards/auth
```
#### Tipos de guards:
- `CanActivate` – Previene acceso a una ruta.
- `CanDeactivate` – Previene salir de una ruta.
- `CanLoad` – Evita que se cargue un módulo.
- `CanActivateChild` – Para rutas hijas.
[[#Example Guard]]
---
### 🧪 Pipe (`ng g pipe`)
#### ¿Qué es un Pipe?
Un **Pipe** transforma datos en la vista. Ejemplo: convertir texto a mayúsculas, formatear fechas, monedas, etc.
#### Comando para generar un pipe:
```bash
ng generate pipe pipes/mayuscula
```
Alias:
```bash
ng g pipe pipes/mayuscula
```
[[#Example Pipe]]   

---
## 📏 Directive (`ng g directive`)
#### ¿Qué es una Directiva?
Una **Directiva** es una clase que modifica el comportamiento o apariencia de un elemento HTML.
#### Comando para generar una directiva:
```bash
ng generate directive directives/resaltar
```
Alias:
```bash
ng generate directive directives/resaltar
```
[[#Example Directive]]

---
# Example Guard
```ts
@Injectable({ providedIn: 'root' })
export class AuthGuard implements CanActivate {
  constructor(private authService: AuthService, private router: Router) {}

  canActivate(): boolean {
    if (this.authService.estaLogueado()) {
      return true;
    }
    this.router.navigate(['/login']);
    return false;
  }
}
```

# Example Pipe
```ts
@Pipe({ name: 'mayuscula' })
export class MayusculaPipe implements PipeTransform {
  transform(value: string): string {
    return value.toUpperCase();
  }
}
```
```HTML
<p>{{ 'angular' | mayuscula }}</p> <!-- Output: ANGULAR -->
```

# Example Directive
```ts
@Directive({ selector: '[appResaltar]' })
export class ResaltarDirective {
  constructor(private el: ElementRef) {
    el.nativeElement.style.backgroundColor = 'yellow';
  }
}
```
```HTML
<p appResaltar>Texto resaltado</p>
```