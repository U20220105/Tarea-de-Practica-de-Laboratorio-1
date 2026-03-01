

# 🏥 hospital project – práctica 1

## modelos y migraciones en asp.net core

---

## 📚 información general

**universidad:** universidad de oriente.

**materia:** desarrollo de páginas activas.

**práctica:** 1.

**tema:** modelos y migraciones en asp.net core.

**docente:** william rodríguez.

**horario de práctica:** martes 4:20pm – 6:00pm.

---

## 🎯 objetivo

desarrollar un proyecto en asp.net core aplicando:

* creación de modelos
* relaciones entre entidades
* uso de entity framework
* migraciones
* conexión a base de datos

---

## ⚙️ tecnologías utilizadas

* asp.net core mvc
* entity framework core
* sql server
* visual studio
* .net 8

---

## 🧩 estructura del sistema

el sistema simula la gestión básica del personal de un hospital.

### entidades creadas

| entidad       | descripción            |
| ------------- | ---------------------- |
| staff         | empleados del hospital |
| staffcategory | categoría del empleado |
| speciality    | especialidad médica    |

---

## 🔗 relaciones

| relación              | tipo                  |
| --------------------- | --------------------- |
| staffcategory → staff | 1 a muchos            |
| speciality → staff    | 1 a muchos (opcional) |

✔ un empleado debe tener categoría
✔ un empleado puede no tener especialidad

---

## 🧠 lógica del sistema

* el sistema usa **soft delete**
* los empleados no se eliminan físicamente
* se usa el campo:

```csharp
IsActive = true
```

para activar o desactivar registros.

---

## 🏗️ configuración del proyecto

### 1. instalación de paquetes

instalar:

```
Microsoft.EntityFrameworkCore
Microsoft.EntityFrameworkCore.SqlServer
Microsoft.EntityFrameworkCore.Tools
```

---

### 2. cadena de conexión

en `appsettings.json`

```json
"ConnectionStrings": {
  "DefaultDbConnection": "Server=.;Database=HospitalDB;Trusted_Connection=True;TrustServerCertificate=True;"
}
```

---

### 3. inyección de dependencias

en `Program.cs`

```csharp
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultDbConnection")));
```

---

## 🗄️ migraciones

### crear migración

```
Add-Migration InitialMigration
```

### actualizar base de datos

```
Update-Database
```

---

## 🧱 tablas generadas

* Staff
* StaffCategories
* Specialities
* __EFMigrationsHistory

---

## 📌 validaciones implementadas

* campos obligatorios
* longitud máxima de texto
* relaciones con llaves foráneas
* especialidad opcional

---

## 🧪 resultado

el sistema permite:

✔ registrar personal
✔ asignar categoría
✔ asignar especialidad opcional
✔ mantener integridad de datos
✔ evitar eliminación física de registros

---

## 📎 aprendizaje obtenido

* uso de modelos
* relaciones en entity framework
* migraciones
* contexto de base de datos
* conexión a sql server

---

## 👨‍💻 autor

U20220105
