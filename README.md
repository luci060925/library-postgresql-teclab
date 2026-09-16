# Library Database

> PostgreSQL library database with PL/pgSQL functions, a trigger, and a view.

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

> Proyecto final — Base de Datos, Teclab, Tecnicatura Superior en Programación (2026).

## Sobre el proyecto

Base de datos completa para la gestión de una biblioteca, implementada en PostgreSQL 18. Incluye tablas relacionadas mediante claves primarias y foráneas, funciones PL/pgSQL, un trigger y una vista, con datos de muestra.

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

- `devolver_libro(p_lector, p_libro)` — registra la devolución de un libro completando la fecha de devolución real del préstamo
- `libros_prestados()` — devuelve la cantidad de préstamos activos (sin devolución registrada)
- `log_devolucion()` — función del trigger que inserta el registro en `logs_devoluciones`

### Trigger

- `trg_log_devolucion` — registra automáticamente en `logs_devoluciones` cada vez que se devuelve un libro

### Vista

- `libros_prestados` — préstamos registrados con los datos del lector y del libro (título, editorial e ISBN)

## Ejecución

**Requisitos:** PostgreSQL 18 (el script fue generado con `pg_dump` 18 y usa instrucciones que no existen en versiones anteriores).

```bash
git clone https://github.com/luci060925/library-postgresql-teclab.git
cd library-postgresql-teclab
psql -U postgres -f teclab_library_database.sql
```

---

**Luciana Mansilla** · [LinkedIn](https://www.linkedin.com/in/luciana-mansilla-854bb5419/) · [GitHub](https://github.com/luci060925)
