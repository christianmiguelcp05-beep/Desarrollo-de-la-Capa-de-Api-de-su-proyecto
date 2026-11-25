#  [NombreProyecto] - Capa API

API REST desarrollada con **ASP.NET Core Web API** para el sistema de gestión hotelera. Expone operaciones CRUD sobre las entidades del proyecto, reutilizando los repositorios construidos en la capa de acceso a datos (DAL).

> Proyecto académico - Instituto Tecnológico de Las Américas (ITLA)
> Asignatura: [Nombre de la asignatura] | Docente: [Nombre del profesor]

##  Equipo

| Integrante | Matrícula | Entidades asignadas |
|---|---|---|
| [Nombre 1] | [Matrícula] | [Hoteles, Pisos] |
| [Nombre 2] | [Matrícula] | [Habilitaciones] |
| [Nombre 3] | [Matrícula] | [Bloques, Tipos de habilitaciones] |

##  Arquitectura

```
[NombreProyecto].sln
├── [NombreProyecto].DAL   → Models, Data (DbContext), Repositories
├── [NombreProyecto].BL    → Services (lógica de negocio)
├── [NombreProyecto].Web   → Capa de presentación
└── [NombreProyecto].Api   → Controllers, DTOs, Program.cs   ← este trabajo
```

Flujo de una petición:

```
Cliente → Controller (API) → Repository (DAL) → Base de datos
```

##  Tecnologías

- .NET [8.0]
- ASP.NET Core Web API
- Entity Framework Core
- SQL Server
- Swagger / OpenAPI
- Visual Studio 2022
- Git y GitHub

##  Instalación y ejecución

1. **Clonar el repositorio**
   ```bash
   git clone [URL-del-repositorio]
   cd [NombreProyecto]
   ```
2. **Cambiar a la rama del módulo**
   ```bash
   git checkout [nombre-de-tu-rama]
   ```
3. **Configurar la cadena de conexión** en `[NombreProyecto].Api/appsettings.json`:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=[SERVIDOR];Database=[BASE_DE_DATOS];Trusted_Connection=True;TrustServerCertificate=True;"
   }
   ```
4. **Restaurar paquetes y ejecutar**
   ```bash
   dotnet restore
   dotnet run --project [NombreProyecto].Api
   ```
5. **Abrir Swagger** en `https://localhost:[puerto]/swagger`

##  Endpoints

Todas las entidades siguen el mismo patrón CRUD.

### Hoteles

| Método | Ruta | Descripción | Respuestas |
|---|---|---|---|
| GET | `/api/hoteles` | Lista todos los hoteles | 200 |
| GET | `/api/hoteles/{id}` | Obtiene un hotel por id | 200, 404 |
| POST | `/api/hoteles` | Crea un hotel | 201, 400 |
| PUT | `/api/hoteles/{id}` | Actualiza un hotel | 204, 400, 404 |
| DELETE | `/api/hoteles/{id}` | Elimina un hotel | 204, 404 |

### Pisos · Habilitaciones · Bloques · Tipos de habilitaciones

Mismo esquema de rutas y respuestas:
`/api/pisos`, `/api/habilitaciones`, `/api/bloques`, `/api/tiposhabilitaciones`

> Ajusta esta sección a las entidades que desarrolló cada integrante.

### Ejemplo de petición

`POST /api/hoteles`

```json
{
  "nombre": "Grand Royale",
  "direccion": "Av. Winston Churchill, Santo Domingo"
}
```

Respuesta `201 Created`:

```json
{
  "id": 1,
  "nombre": "Grand Royale",
  "direccion": "Av. Winston Churchill, Santo Domingo"
}
```

##  Validaciones y manejo de errores

- Uso de DTOs para no exponer los modelos de Entity Framework.
- Validaciones con DataAnnotations (`Required`, `StringLength`, `Range`).
- Verificación de llaves foráneas antes de crear o actualizar (por ejemplo, que el hotel exista al crear un piso).
- Códigos HTTP: `200`, `201`, `204`, `400`, `404`.

##  Evidencias

-  Documento PDF: [enlace o ruta en el repositorio, ej. `/docs/evidencia.pdf`]
-  Video de demostración: [enlace al video]

##  Flujo de trabajo con Git

- Una rama por módulo/integrante: `feature/[entidad]-api`
- Commits pequeños y descriptivos.
- Integración a la rama principal mediante Pull Request.

##  Licencia

Proyecto con fines educativos.
