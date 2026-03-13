# Sistema de Gestión de Citas Médicas

API REST desarrollada con **ASP.NET Core (.NET 8)** para administrar
pacientes, médicos y citas médicas.

Este proyecto fue desarrollado como parte del curso de **Servicios Web**
en la **Escuela de Educación Superior Tecnológica Privada IDAT**.

------------------------------------------------------------------------

# Descripción del Proyecto

El sistema consiste en una **API RESTful** que permite gestionar
información relacionada con:

-   Pacientes
-   Médicos
-   Citas médicas

La API implementa operaciones **CRUD (Create, Read, Update, Delete)**
para cada entidad del sistema mediante endpoints HTTP.

Las principales funcionalidades incluyen:

-   Registro de pacientes
-   Registro de médicos
-   Programación de citas médicas
-   Consulta de registros
-   Actualización de información
-   Eliminación de registros

------------------------------------------------------------------------

# Tecnologías Utilizadas

-   .NET 8
-   ASP.NET Core Web API
-   C#
-   Postman (para pruebas)
-   GitHub (repositorio del proyecto)

------------------------------------------------------------------------

# Requisitos del Sistema

Antes de ejecutar el proyecto es necesario instalar:

-   **.NET SDK 8.0 o superior**
-   **Git**
-   **Postman** (opcional, para probar la API)
-   **Visual Studio 2022** o **Visual Studio Code**

------------------------------------------------------------------------

# Instalación del Proyecto

Siga los siguientes pasos para instalar y ejecutar el proyecto.

## 1. Clonar el repositorio

``` bash
git clone https://github.com/RuisuTech/Proyecto-Clinica
```

## 2. Ingresar al directorio del proyecto

``` bash
cd Proyecto-Clinica
```

## 3. Restaurar dependencias

``` bash
dotnet restore
```

## 4. Ejecutar la aplicación

``` bash
dotnet run
```

La API se ejecutará normalmente en:

    http://localhost:5289

------------------------------------------------------------------------

# Estructura del Proyecto

El proyecto sigue una arquitectura modular basada en ASP.NET Core.

    /Controllers
        PacientesController.cs
        MedicosController.cs
        CitasController.cs

    /Models
        Paciente.cs
        Medico.cs
        Cita.cs

    /Middleware
        ErrorHandlingMiddleware.cs

    Program.cs

### Controllers

Gestionan las solicitudes HTTP y exponen los endpoints de la API.

### Models

Representan las entidades del sistema:

-   Paciente
-   Medico
-   Cita

### Middleware

El middleware **ErrorHandlingMiddleware** captura errores globales y
devuelve respuestas estructuradas en JSON.

------------------------------------------------------------------------

# Endpoints Principales

## Pacientes

  Método   Endpoint          Descripción
  -------- ----------------- ---------------------
  GET      /pacientes        Listar pacientes
  POST     /pacientes        Registrar paciente
  PUT      /pacientes/{id}   Actualizar paciente
  DELETE   /pacientes/{id}   Eliminar paciente

## Médicos

  Método   Endpoint   Descripción
  -------- ---------- ------------------
  GET      /medicos   Listar médicos
  POST     /medicos   Registrar médico

## Citas

  Método   Endpoint      Descripción
  -------- ------------- -----------------
  GET      /citas        Listar citas
  POST     /citas        Registrar cita
  PUT      /citas/{id}   Actualizar cita
  DELETE   /citas/{id}   Eliminar cita

------------------------------------------------------------------------

# Pruebas con Postman

Las pruebas de la API pueden realizarse mediante **Postman** enviando
solicitudes HTTP a los endpoints correspondientes.

Ejemplos de pruebas realizadas:

-   Registro de paciente (POST)
-   Consulta de pacientes (GET)
-   Registro de médico (POST)
-   Registro de cita médica (POST)
-   Actualización de cita (PUT)
-   Eliminación de registro (DELETE)

------------------------------------------------------------------------

# Equipo de Desarrollo

  Integrante                             Rol
  -------------------------------------- ------------------------------
  Velarde Robles Francisco Xavier Leon   Desarrollo backend
  Colina Martin Jesus Gabriel            Controladores y validaciones
  Roman Huaman Josled Luis Antonio       Modelos de datos
  Peña Chavez Gissel Melani              Pruebas con Postman
  Osorio Guzman Jose Luis                Documentación y repositorio

------------------------------------------------------------------------

# Repositorio del Proyecto

Repositorio oficial:

https://github.com/RuisuTech/Proyecto-Clinica

------------------------------------------------------------------------

# Conclusiones

Este proyecto demuestra la implementación de una **API REST utilizando
ASP.NET Core**, aplicando:

-   Arquitectura modular
-   Manejo de errores con middleware
-   Validación de datos
-   Operaciones CRUD
-   Pruebas funcionales con Postman

La solución puede ampliarse en el futuro con:

-   Base de datos (SQL Server o PostgreSQL)
-   Autenticación con JWT
-   Interfaz web o aplicación móvil
