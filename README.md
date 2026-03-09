# ToDoApi - Ejemplo .NET Web API con PostgreSQL

Proyecto de ejemplo minimalista que expone una API REST para gestionar tareas (ToDo) y usa PostgreSQL vía EF Core.

Instrucciones rápidas:

- Restaurar dependencias:

```bash
dotnet restore ToDoApi/ToDoApi.csproj
```

- Compilar:

```bash
dotnet build ToDoApi/ToDoApi.csproj
```

- Ejecutar:

```bash
dotnet run --project ToDoApi/ToDoApi.csproj
```

La cadena de conexión por defecto está en `ToDoApi/appsettings.json`.

Notas:
- El proyecto usa `EnsureCreated()` para crear las tablas automáticamente en la base de datos si no existen.
- Para producción use migraciones EF Core en lugar de `EnsureCreated()`.

Endpoints disponibles:
- GET  /api/todo
- GET  /api/todo/{id}
- POST /api/todo
- PUT  /api/todo/{id}
- DELETE /api/todo/{id}
