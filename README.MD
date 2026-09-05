# ClinicaAPI

API REST desarrollada con **ASP.NET Core (.NET 8)** para la gestión de
pacientes, médicos y citas médicas en una clínica.

Proyecto académico desarrollado como parcial del curso de **Servicios
Web** en la **Escuela de Educación Superior Tecnológica Privada IDAT**.

---

## Descripción

API RESTful que permite gestionar información de una clínica
implementando operaciones **CRUD** para cada entidad. Los datos se
almacenan **en memoria** (sin base de datos).

### Entidades

- **Paciente**: nombre, DNI, teléfono, fecha de nacimiento, dirección
- **Médico**: nombre, especialidad, CMP, teléfono, email
- **Cita**: paciente, médico, fecha/hora, duración, estado, motivo,
  observaciones (con auditoría de fechas y eliminación lógica)

### Funcionalidades

- Registro, consulta, actualización y eliminación de pacientes
- Registro, consulta, actualización y eliminación de médicos
- Programación de citas con validación de existencia de paciente y
  médico
- Estados de cita: Programada, Confirmada, Cancelada, Atendida
- Eliminación lógica de citas (soft delete)
- Manejo global de errores con middleware personalizado
- Documentación interactiva con Swagger/OpenAPI

---

## Tecnologías

- .NET 8
- ASP.NET Core Web API
- C#
- Swagger / Swashbuckle
- Postman (para pruebas)
- GitHub

---

## Requisitos

- **.NET SDK 8.0** o superior
- **Git**
- **Postman** (opcional, para probar la API)
- **Visual Studio 2022** o **Visual Studio Code**

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/RuisuTech/Proyecto-Clinica.git
cd Proyecto-Clinica
```

### 2. Restaurar dependencias

```bash
dotnet restore
```

### 3. Ejecutar la aplicación

```bash
dotnet run
```

La API estará disponible en:

    http://localhost:5289

La documentación Swagger se abre automáticamente al iniciar en
modo desarrollo:

    http://localhost:5289/swagger

---

## Estructura del Proyecto

```
/
├── Controllers/
│   ├── ControllerPacientes.cs   # Endpoints de pacientes
│   ├── ControllerMedicos.cs     # Endpoints de médicos
│   └── ControllerCitas.cs       # Endpoints de citas
├── Models/
│   ├── Paciente.cs              # Modelo Paciente
│   ├── Medico.cs                # Modelo Médico
│   └── Citas.cs                 # Modelo Cita + FechaAuditorias + EstadoCita
├── Middleware/
│   └── ErrorHandlingMiddleware.cs  # Manejo global de errores
├── Properties/
│   └── launchSettings.json
├── Program.cs                   # Configuración de la aplicación
├── appsettings.json
└── PARCIAL-00.csproj
```

### Controllers

Gestionan las solicitudes HTTP y exponen los endpoints de la API. Cada
controller contiene operaciones CRUD completas con validaciones.

### Models

Entidades del sistema con validaciones usando `DataAnnotations`:

- **Paciente**: campos obligatorios con formato de DNI (8 dígitos),
  teléfono y nombre (solo letras)
- **Medico**: incluye CMP (5-7 dígitos), especialidad y email
- **Cita**: hereda de `FechaAuditorias`, incluye enum `EstadoCita`
  con valores: Programada, Confirmada, Cancelada, Atendida

### Middleware

`ErrorHandlingMiddleware` captura excepciones no controladas y devuelve
respuestas JSON estructuradas con código HTTP 500.

---

## Endpoints

### Pacientes

| Método  | Endpoint               | Descripción          |
|---------|------------------------|----------------------|
| GET     | `/api/pacientes`       | Listar pacientes     |
| GET     | `/api/pacientes/{id}`  | Obtener paciente     |
| POST    | `/api/pacientes`       | Registrar paciente   |
| PUT     | `/api/pacientes/{id}`  | Actualizar paciente  |
| DELETE  | `/api/pacientes/{id}`  | Eliminar paciente    |

### Médicos

| Método  | Endpoint               | Descripción          |
|---------|------------------------|----------------------|
| GET     | `/api/medicos`         | Listar médicos       |
| GET     | `/api/medicos/{id}`    | Obtener médico       |
| POST    | `/api/medicos`         | Registrar médico     |
| PUT     | `/api/medicos/{id}`    | Actualizar médico    |
| DELETE  | `/api/medicos/{id}`    | Eliminar médico      |

### Citas

| Método  | Endpoint               | Descripción          |
|---------|------------------------|----------------------|
| GET     | `/api/citas`           | Listar citas         |
| GET     | `/api/citas/{id}`      | Obtener cita         |
| POST    | `/api/citas`           | Registrar cita       |
| PUT     | `/api/citas/{id}`      | Actualizar cita      |
| DELETE  | `/api/citas/{id}`      | Eliminar cita (soft) |

> **Nota**: Las citas eliminadas se marcan con `FechaEliminacion` y no
> aparecen en el listado GET, pero persisten en memoria.

---

## Equipo de Desarrollo

| Integrante                            | Rol                         |
|---------------------------------------|-----------------------------|
| Velarde Robles Francisco Xavier Leon  | Desarrollo backend          |
| Colina Martin Jesus Gabriel           | Controladores y validaciones|
| Roman Huaman Josled Luis Antonio      | Modelos de datos            |
| Peña Chavez Gissel Melani             | Pruebas con Postman         |
| Osorio Guzman Jose Luis               | Documentación y repositorio |

---

## Repositorio

<https://github.com/RuisuTech/Proyecto-Clinica>

---

## Futuras mejoras

- Integración con base de datos (SQL Server o PostgreSQL)
- Autenticación y autorización con JWT
- Paginación y filtros en los endpoints de consulta
- Interfaz web o aplicación móvil
