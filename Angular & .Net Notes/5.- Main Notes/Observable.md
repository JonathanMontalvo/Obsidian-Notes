2025-05-25 19:38

tags:[Angular],[RxJS],[subscribe]

---
# ¿Qué es un Observable y cómo se usa?
### 📦 ¿Qué es un Observable?
Un **Observable** es una forma de manejar datos **asincrónicos** en Angular, usando la librería **RxJS**. Es como una **fuente de datos** que puede emitir múltiples valores a lo largo del tiempo (similar a un `Promise`, pero más flexible).

> En Angular, todo lo relacionado con peticiones HTTP, formularios reactivos, eventos y estados se basa en **Observables**.

---
### 🔄 Comparación rápida

|Tipo|Entrega|Puede emitir varios|Cancelable|Soporta operadores|
|---|---|---|---|---|
|`Promise`|Una vez|❌ No|❌ No|❌ No|
|`Observable`|Varias veces|✅ Sí|✅ Sí|✅ Sí|
[[#📌 Ejemplo básico (RxJS puro)]]

---
### 🧩 `subscribe()` - Cómo consumir un Observable
Cuando usas un servicio como `HttpClient`, recibes un Observable. Para acceder a sus valores, necesitas **suscribirte** con `.subscribe()`.

En Angular (y en general con **RxJS**), el método `.subscribe()` recibe un **observer**, que puede tener **tres funciones opcionales**:
```ts
observable.subscribe({
  next: (valor) => { ... },      // cuando llega un dato
  error: (err) => { ... },       // si ocurre un error
  complete: () => { ... }        // cuando el observable termina
});
```
### 🧠 ¿Cuándo usar `{ next, error, complete }`?

Usas el **objeto completo** cuando:
- Quieres manejar **errores** explícitamente (evitar que rompa la app).
- Necesitas hacer algo al **terminar** la secuencia (por ejemplo: cerrar un modal, mostrar mensaje, detener un loading spinner).
- Quieres mantener todo **más claro y separado**.

>💡 **Recomendación profesional**: usa el objeto `{ next, error, complete }` cuando trabajas con **servicios HTTP** o lógica que podría fallar. Es más robusto y escalable.

[[#✔️Ejemplo de Observable]]

---
# Example
## 📌 Ejemplo básico (RxJS puro)

```ts
import { Observable } from 'rxjs';

const observable$ = new Observable<string>((observer) => {
  observer.next('Hola');
  observer.next('Mundo');
  observer.complete();
});

observable$.subscribe({
  next: (valor) => console.log(valor),
  complete: () => console.log('¡Completado!')
});
```

## ✔️Ejemplo de Observable
```ts
this.service.get().subscribe({
  next: (data) => this.usuarios = data,
  error: (err) => console.error('Error:', err),
  complete: () => console.log('Petición completada')
});
```
---