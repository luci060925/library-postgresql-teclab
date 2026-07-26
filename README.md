# 📚 Library Database – Final Project
### Teclab – Programming Degree  
**Author:** Luciana Mansilla  
**Year:** 2026  

This repository contains the **Final Project for the Database assignature**, built entirely in **PostgreSQL 18**.  
It implements a complete library management database with tables, relationships, functions, triggers, views, and real sample data according to the academic requirements.

---

# 🚀 Project Contents

The file **`teclab_library_database.sql`** includes:

### ✔️ Full database structure
- **lectores** (readers)
- **libros** (books)
- **alquileres** (rentals)
- **logs_devoluciones** (return logs – Activity 4 requirement)
- Primary and foreign keys
- Sequences and auto-increment settings
- View: **libros_prestados**

### ✔️ Data included
- 10 readers  
- 10 books  
- Rental records  
- Automatic logs generated through triggers during book returns  

### ✔️ PL/pgSQL Functions
- `devolver_libro(p_lector, p_libro)`  
  Updates the real return date for a book rental.

- `libros_prestados()`  
  Returns the total number of books currently rented out.

- `log_devolucion()`  
  Trigger function that logs every book return.

### ✔️ Trigger
- `trg_log_devolucion`  
  Executes **AFTER UPDATE** on `alquileres`, detecting when a real return date is entered and creating a log entry automatically.

---

# 🛠️ How to Restore the Database

## Option 1 — Using pgAdmin
1. Create a new database named **biblioteca**  
2. Right-click → **Restore**  
3. Select the file `teclab_library_database.sql`  
4. Restore

## Option 2 — Using terminal
```bash
createdb -U postgres biblioteca
psql -U postgres -d biblioteca -f teclab_library_database.sql
```

---

# ✅ Testing the Setup

After restoring, verify everything works:

```sql
-- See currently rented books (view)
SELECT * FROM libros_prestados;

-- Register a return
SELECT devolver_libro(1, 1);

-- Check the auto-generated log (trigger)
SELECT * FROM logs_devoluciones;

-- Count books currently rented out (function)
SELECT libros_prestados();
```

---

# 📁 Project Structure

```
library-postgresql-teclab/
├── teclab_library_database.sql   # Full schema, functions, triggers, views and sample data
└── README.md
```

---

# 🛑 Requirements
- PostgreSQL 15+ (developed and tested on PostgreSQL 18)
- `psql` CLI or pgAdmin

---

*Final Project for the Database course — Teclab (2026).*
