# Library Database

> PostgreSQL library database with PL/pgSQL functions, triggers, and views.

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

> Proyecto final — Base de Datos, Teclab, Tecnicatura Superior en Programación (2026).

## Sobre el proyecto

Base de datos completa para la gestión de una biblioteca, implementada en PostgreSQL 18. Incluye tablas relacionales, funciones PL/pgSQL, triggers y vistas con datos de muestra reales.

## Contenido del proyecto

El archivo `teclab_library_database.sql` incluye:

### Estructura

| Tabla | Descripción |
|---|---|
| `lectores` | Socios de la biblioteca |
| `libros` | Catálogo de libros |
| `alquileres` | Registro de préstamos |
| `logs_devoluciones` | Log automático de devoluciones (trigger) |

### Funciones PL/pgSQL

- Registro de préstamos con validación de disponibilidad
- Registro de devoluciones con actualización de estado
- Consulta de libros disponibles
- Listado de préstamos activos por lector

### Triggers

- `trg_log_devolucion` — registra automáticamente en `logs_devoluciones` cada vez que se devuelve un libro

### Vistas

- `libros_prestados` — libros actualmente en préstamo con datos del lector

## Ejecución

**Requisitos:** PostgreSQL 14+.

```bash
git clone https://github.com/luci060925/library-postgresql-teclab.git
cd library-postgresql-teclab
psql -U postgres -f teclab_library_database.sql
```

---

**Luciana Mansilla** · [LinkedIn](https://www.linkedin.com/in/luciana-mansilla-854bb5419/) · [GitHub](https://github.com/luci060925)
