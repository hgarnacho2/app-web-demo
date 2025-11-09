# ⚽ TFM - Demo de Autenticación y Filtrado (Clubes de Fútbol)

Este repositorio contiene dos páginas HTML estáticas diseñadas para simular un flujo básico de autenticación y acceso a contenido restringido. 

## 🔗 Acceso al Despliegue

Las páginas están diseñadas para ser servidas como archivos estáticos través de GitHub Pages.

| Archivo | URL de Acceso | Descripción |
| :--- | :--- | :--- |
| **`login.html`** | `/login.html` | Página de inicio de sesión. |
| **`private.html`** | `/private.html` | Zona privada con la lista de clubes (requiere autenticación). |

> **Nota:** La URL base es la siguiente:
* https://hgarnacho2.github.io/app-web-demo/login.html

---

## 🔐 `login.html`: Funcionalidad de Autenticación

La página de inicio de sesión implementa una lógica de autenticación simple y completamente contenida en JavaScript.

### Credenciales de Prueba

Utiliza las siguientes credenciales y requisitos para realizar un inicio de sesión exitoso:

| Campo | Valor Requerido | Observación |
| :--- | :--- | :--- |
| **Nombre de usuario** | `user` | Sensible a mayúsculas/minúsculas. |
| **Contraseña** | `password` | Sensible a mayúsculas/minúsculas. |
| **Términos de uso** | Debe estar **marcado** | Obligatorio para el inicio de sesión. |

### Flujo de Navegación

1.  Si el inicio de sesión es exitoso, la página redirige a `private.html` después de 1 segundo.
2.  La redirección incluye parámetros de autenticación en la URL (`?auth=true&user=...`).

---

## 🛡️ `private.html`: Zona Privada y Datos

Esta página simula una zona de contenido exclusivo, ofreciendo una tabla interactiva de datos.

### Acceso Restringido

La página comprueba la existencia del parámetro `auth=true` en la URL. Si no se detecta, el usuario es **redirigido inmediatamente a `login.html`**.

### Contenido y Funcionalidades

La página carga una lista de 25 clubes de fútbol españoles.

* **Búsqueda (Filtro):** El campo de entrada con `id="searchInput"` permite filtrar la tabla en tiempo real por **nombre del club** o **ciudad**.
* **Paginación:** La tabla está paginada, mostrando **10 clubes por página**.
* **Cerrar Sesión:** El botón con `id="logoutBtn"` redirige al usuario de vuelta a `login.html`.

---

## 🧪 Notas para la Automatización (E2E)

Las siguientes propiedades se han incluido en el diseño de las páginas para facilitar la creación de tests automatizados con herramientas como Playwright:

* Todos los campos de entrada y botones clave tienen **ID's únicos** (`#username`, `#password`, `#terms`, `#logoutBtn`, `#searchInput`).
* Los mensajes de error y éxito de la autenticación se muestran en el elemento con `id="errorMessage"`.
* La tabla de resultados es fácilmente accesible mediante `id="clubsTable"`.

El código de estas páginas es estable y es un objetivo predecible para ejercicios de automatización de pruebas.