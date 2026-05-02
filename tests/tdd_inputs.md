# TDD — Test de Inputs
## QA for Indie Devs

**Proyecto:** QA for Indie Devs  
**Tipo de documento:** Test Design Document — Validación de Entradas  
**Ubicación en el repositorio:** `tests/tdd_inputs.md`  
**Fecha:** Abril 2026

---

## Funcionalidades cubiertas

| ID | Funcionalidad |
|----|---------------|
| F-01 | Registro de usuario |
| F-02 | Inicio de sesión |
| F-03 | Subida de juego |

---

## Tipos de prueba

| Tipo | Descripción |
|------|-------------|
| ✅ Positiva | La entrada es válida y el sistema responde correctamente |
| ❌ Negativa | La entrada es inválida y el sistema muestra un error |
| ⚠️ Límite | La entrada está en el borde del rango aceptado |

---

## F-01 — Registro de usuario

### TC-F01-01 — Registro exitoso con datos válidos

| Campo | Detalle |
|-------|---------|
| **Descripción** | El usuario completa todos los campos correctamente |
| **Precondición** | El correo no existe en el sistema |
| **Entrada** | `nombre`: "Carlos Pérez", `correo`: "carlos@correo.com", `contrasena`: "pass123", `confirmarContrasena`: "pass123" |
| **Resultado esperado** | Cuenta creada. El sistema envía un correo de confirmación con enlace válido por 24 horas |
| **Tipo** | ✅ Positiva |

---

## F-02 — Inicio de sesión

### TC-F02-01 — Bloqueo tras 5 intentos fallidos

| Campo | Detalle |
|-------|---------|
| **Descripción** | El usuario falla 5 veces consecutivas al ingresar su contraseña |
| **Precondición** | La cuenta existe y no está bloqueada |
| **Entrada** | 5 intentos con `contrasena` incorrecta |
| **Resultado esperado** | El sistema bloquea el acceso por 10 minutos y muestra un aviso |
| **Tipo** | ⚠️ Límite |

---

## F-03 — Subida de juego

### TC-F03-01 — Archivo con extensión no permitida

| Campo | Detalle |
|-------|---------|
| **Descripción** | El usuario intenta subir un archivo en formato no soportado |
| **Precondición** | El usuario ha iniciado sesión |
| **Entrada** | Archivo: `mi_juego.rar` |
| **Resultado esperado** | Mensaje: *"Formato no soportado. Sube un archivo .zip o una URL válida"* |
| **Tipo** | ❌ Negativa |

---

## Resumen

| Funcionalidad | Casos | ✅ | ❌ | ⚠️ |
|---------------|:-----:|:--: |:--:|:--:|
| F-01 Registro |   1   |  1  | 0  | 0 |
| F-02 Login    |   1   |  0  | 0  | 1 |
| F-03 Subida   |   1   |  0  | 1  | 0 |
| **Total**     |  *3*  | *1* | *1*| *1* |

---

Francisco Morales Garcia — QA for indie devs 2026*