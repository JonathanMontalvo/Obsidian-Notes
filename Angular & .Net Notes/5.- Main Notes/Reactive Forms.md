2025-05-25 19:54

tags:[angular],[forms],[reactive forms]

---
# Reactive Forms
## 🧠Formulario Reactivo Avanzado (FormGroup + FormArray)
### 🎯 Objetivo
Crear un formulario reactivo con:
- `FormGroup`, `FormControl`, `FormArray`
- Validadores simples y múltiples
- Acceso a valores y estados (`get`, `at`)
- Binding al template (`[formGroup]`, `formControlName`)
- Deshabilitar / habilitar campos
---
## 🧩 1. Imports necesarios

```ts
import { FormBuilder, FormGroup, FormArray, FormControl, Validators } from '@angular/forms';
```
---
## 🔧 2. Declarar Formulario Reactivo

```ts
formulario: FormGroup;

nombreValidators = Validators.compose([
  Validators.required,
  Validators.minLength(3)
]);

correoValidators = Validators.compose([
  Validators.required,
  Validators.email
]);

telefonoValidators = Validators.compose([
  Validators.required,
  Validators.pattern('[0-9]{10}')
]);

constructor(private fb: FormBuilder) {
  this.formulario = this.fb.group({
    nombre: this.fb.control('', this.nombreValidators),
    correo: this.fb.control('', this.correoValidators),
    telefonos: this.fb.array([this.crearTelefonoControl()]),
    contactos: this.fb.array([this.crearContactoGroup()])
  });
```
---
### 🧱 Métodos constructores
#### ☑️ FormControl simple para telefonos
```ts
crearTelefonoControl(): FormControl {
  return this.fb.control('', this.telefonoValidators);
}
```
### 👥 FormGroup para contactos
```ts
crearContactoGroup(): FormGroup {
  return this.fb.group({
    nombre: ['', Validators.required],
    relacion: ['']
  });
}
```
### 🧬 FormArray de FormArray → contiene un FormGroup
```ts
crearMatriz(): FormArray {
  return this.fb.array([
    this.fb.group({
      campo1: ['', Validators.required],
      campo2: ['']
    })
  ]);
}
```
---
## 🧠 Getters para acceso limpio
```ts
get nombre() {
  return this.formulario.get('nombre') as FormControl;
}

get correo() {
  return this.formulario.get('correo') as FormControl;
}

get telefonos(): FormArray {
  return this.formulario.get('telefonos') as FormArray;
}

get contactos(): FormArray {
  return this.formulario.get('contactos') as FormArray;
}

get matrices(): FormArray {
  return this.formulario.get('matrices') as FormArray;
}
```
---
## ➕ Métodos para agregar dinámicamente
```ts
agregarTelefono(): void {
  this.telefonos.push(this.crearTelefonoControl());
}

agregarContacto(): void {
  this.contactos.push(this.crearContactoGroup());
}

agregarFilaMatriz(index: number): void {
  const matriz = this.matrices.at(index) as FormArray;
  matriz.push(this.fb.group({
    campo1: [''],
    campo2: ['']
  }));
}

agregarMatriz(): void {
  this.matrices.push(this.crearMatriz());
}
```
---
## 📥 Acceder a valores con `get`, `at`
```ts
this.nombre.value
this.formulario.get('contactos')?.value
this.contactos.at(0).get('nombre')?.value
(this.matrices.at(0) as FormArray).at(1).get('campo1')?.value
```
---
## 🚫 Deshabilitar / habilitar
```ts
this.nombre.disable();
this.telefonos.at(0).disable();
this.contactos.at(1).get('relacion')?.disable();
```
---
## 🧼 setValue y patchValue
```ts
this.nombre.setValue('Juan');
this.contactos.at(0).patchValue({ nombre: 'María' });
```
---
### 📝 ¿Bindeo en HTML?
Ejemplo `FormArray` de `FormGroup`:
```ts
<div formArrayName="contactos">
  <div *ngFor="let contacto of contactos.controls; let i = index" [formGroupName]="i">
    <input formControlName="nombre" placeholder="Nombre del contacto">
    <input formControlName="relacion" placeholder="Relación">
  </div>
</div>
```
---