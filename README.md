# 🚀 Django Multi-App Project: API Biblioteca & Airport Distance

Este repositorio contiene dos aplicaciones desarrolladas con Django y Django REST Framework, enfocadas en la gestión eficiente de bases de datos y el consumo de interfaces web modernas.

---

## 📚 App 1: API REST de Biblioteca (`api_rest_biblioteca`)

Una API robusta para gestionar el inventario y los préstamos de una biblioteca. Desarrollada con Django REST Framework (DRF).

### ✨ Características Principales
* **Gestión de Autores y Libros:** Endpoints para crear, leer, actualizar y eliminar (CRUD) registros.
* **Sistema de Préstamos:** * Lógica automatizada: Al registrar un préstamo, el libro pasa automáticamente a estado "No disponible".
    * Endpoints personalizados (`@action`) para `prestar/` y `devolver/` libros.
* **Validaciones Nativas:** Validación estricta para que el ISBN de los libros contenga exactamente 13 caracteres.
* **Filtros y Búsqueda:** Implementación de `DjangoFilterBackend`, `SearchFilter` y `OrderingFilter` para realizar búsquedas avanzadas (por género, disponibilidad, nacionalidad del autor, etc.).
* **Seguridad:** Restricción de consultas (`get_queryset`) para que los usuarios estándar solo puedan ver su propio historial de préstamos, mientras que el Staff tiene acceso total.
* **Paginación:** Configurada globalmente para devolver resultados en bloques de 10 elementos.

### 🛣️ Rutas Principales (Endpoints)
Base URL: `/api/`
* `GET/POST /api/autores/` - Gestión de autores.
* `GET/POST /api/libros/` - Gestión de libros.
* `GET /api/libros/disponibles/` - Lista filtrada de libros listos para préstamo.
* `POST /api/libros/{id}/prestar/` - Registra un préstamo a nombre del usuario autenticado.
* `POST /api/prestamos/{id}/devolver/` - Marca un préstamo como devuelto y libera el libro.

---

## ✈️ App 2: Calculadora de Distancia entre Aeropuertos (`airports`)

Una interfaz web para calcular distancias entre cualquier par de aeropuertos del mundo usando sus códigos IATA.

### ✨ Características Principales
* **Formularios Seguros:** Uso de Django Forms para capturar y limpiar los datos de entrada.
* **Validación Estricta:** * Verificación en frontend con atributos HTML5 (`pattern="[A-Z]{3}"`).
    * Verificación en backend (`clean_aeropuerto_origen`) asegurando que solo se procesen caracteres alfabéticos y se conviertan a mayúsculas.
* **Resultados Multimétrica:** Retorna las distancias calculadas en Kilómetros, Millas y Millas Náuticas (Nudos).
* **UI/UX Premium:** Interfaz responsiva diseñada con Bootstrap 5, tarjetas con diseño moderno, y visualización clara de errores y resultados.

---

## 🛠️ Tecnologías Utilizadas

* **Backend:** Python 3, Django, Django REST Framework.
* **Base de Datos:** SQLite (por defecto en desarrollo) / Relaciones ForeignKey avanzadas (`select_related`).
* **Frontend:** HTML5, CSS3, Bootstrap 5.
* **Herramientas Extra:** `django-filter` para parámetros avanzados en la API.

## ⚙️ Instalación y Configuración Local

1. Clona este repositorio:
   ```bash
   git clone <url-del-repositorio>