# UniversityPortal - Proyecto Full Stack (.NET Web API + Angular)

Este proyecto es una aplicación web educativa construida con **ASP.NET Core Web API** y **Angular**. Permite visualizar estudiantes, materias y profesores asociados.


## Script para Portal Universitario

```sql
USE [master]
GO
/****** Object:  Database [UniversityPortalDB]    Script Date: 5/26/2025 8:17:37 AM ******/
CREATE DATABASE [UniversityPortalDB]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'UniversityPortalDB', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.SQLEXPRESS\MSSQL\DATA\UniversityPortalDB.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'UniversityPortalDB_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.SQLEXPRESS\MSSQL\DATA\UniversityPortalDB_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT
GO
ALTER DATABASE [UniversityPortalDB] SET COMPATIBILITY_LEVEL = 150
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [UniversityPortalDB].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [UniversityPortalDB] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET ARITHABORT OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET AUTO_CLOSE ON 
GO
ALTER DATABASE [UniversityPortalDB] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [UniversityPortalDB] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [UniversityPortalDB] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET  ENABLE_BROKER 
GO
ALTER DATABASE [UniversityPortalDB] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [UniversityPortalDB] SET READ_COMMITTED_SNAPSHOT ON 
GO
ALTER DATABASE [UniversityPortalDB] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [UniversityPortalDB] SET  MULTI_USER 
GO
ALTER DATABASE [UniversityPortalDB] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [UniversityPortalDB] SET DB_CHAINING OFF 
GO
ALTER DATABASE [UniversityPortalDB] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [UniversityPortalDB] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [UniversityPortalDB] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [UniversityPortalDB] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [UniversityPortalDB] SET QUERY_STORE = OFF
GO
USE [UniversityPortalDB]
GO
/****** Object:  Table [dbo].[__EFMigrationsHistory]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[__EFMigrationsHistory](
	[MigrationId] [nvarchar](150) NOT NULL,
	[ProductVersion] [nvarchar](32) NOT NULL,
 CONSTRAINT [PK___EFMigrationsHistory] PRIMARY KEY CLUSTERED 
(
	[MigrationId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Students]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Students](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[username] [nvarchar](max) NOT NULL,
	[Age] [int] NOT NULL,
	[FirstName] [nvarchar](max) NOT NULL,
	[LastName] [nvarchar](max) NOT NULL,
	[rolestudent] [int] NOT NULL,
	[Password] [nvarchar](max) NOT NULL,
 CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[StudentSubject]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[StudentSubject](
	[StudentId] [int] NOT NULL,
	[SubjectId] [int] NOT NULL,
	[TeacherId] [int] NOT NULL,
 CONSTRAINT [PK_StudentSubject] PRIMARY KEY CLUSTERED 
(
	[StudentId] ASC,
	[SubjectId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Subjects]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Subjects](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [nvarchar](max) NOT NULL,
	[Credits] [int] NOT NULL,
 CONSTRAINT [PK_Subjects] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Teachers]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Teachers](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [nvarchar](max) NOT NULL,
 CONSTRAINT [PK_Teachers] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[TeacherSubject]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[TeacherSubject](
	[TeacherId] [int] NOT NULL,
	[SubjectId] [int] NOT NULL,
 CONSTRAINT [PK_TeacherSubject] PRIMARY KEY CLUSTERED 
(
	[TeacherId] ASC,
	[SubjectId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 5/26/2025 8:17:37 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Username] [nvarchar](max) NOT NULL,
	[Password] [nvarchar](max) NOT NULL,
	[Role] [nvarchar](max) NOT NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522162645_firstmigration22052025', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522180443_createSubjectTable', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522190351_createTeacherTable', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522195504_createIntermediateTables', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522223439_updateTeacherTable', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250522234736_updateTeacherTableNew', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523020050_createUserTable', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523151746_rolestudent', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523153833_rolestudentv1', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523154643_rolestudentv2', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523160108_studenttablepw', N'9.0.5')
INSERT [dbo].[__EFMigrationsHistory] ([MigrationId], [ProductVersion]) VALUES (N'20250523161811_updateusername', N'9.0.5')
GO
SET IDENTITY_INSERT [dbo].[Students] ON 

INSERT [dbo].[Students] ([Id], [username], [Age], [FirstName], [LastName], [rolestudent], [Password]) VALUES (20, N'Anderson', 29, N'Anderson', N'Gordillo', 49, N'1234')
INSERT [dbo].[Students] ([Id], [username], [Age], [FirstName], [LastName], [rolestudent], [Password]) VALUES (21, N'admin', 0, N'admin', N'admin', 49, N'0000')
INSERT [dbo].[Students] ([Id], [username], [Age], [FirstName], [LastName], [rolestudent], [Password]) VALUES (31, N'Maria', 23, N'Mariana', N'Lopez', 49, N'1234')
INSERT [dbo].[Students] ([Id], [username], [Age], [FirstName], [LastName], [rolestudent], [Password]) VALUES (32, N'Pedro', 25, N'Pedro', N'Gonzales', 49, N'1234')
INSERT [dbo].[Students] ([Id], [username], [Age], [FirstName], [LastName], [rolestudent], [Password]) VALUES (33, N'Lucas', 20, N'Lucas', N'Martinez', 49, N'1234')
SET IDENTITY_INSERT [dbo].[Students] OFF
GO
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (20, 1, 1)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (31, 6, 3)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (31, 8, 4)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (31, 10, 5)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (32, 1, 1)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (32, 4, 2)
INSERT [dbo].[StudentSubject] ([StudentId], [SubjectId], [TeacherId]) VALUES (32, 6, 3)
GO
SET IDENTITY_INSERT [dbo].[Subjects] ON 

INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (1, N'Mathematics', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (2, N'Physics', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (3, N'Chemistry', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (4, N'Biology', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (5, N'History', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (6, N'Geography', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (7, N'Computer Science', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (8, N'Philosophy', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (9, N'Economics', 3)
INSERT [dbo].[Subjects] ([Id], [Name], [Credits]) VALUES (10, N'Literature', 3)
SET IDENTITY_INSERT [dbo].[Subjects] OFF
GO
SET IDENTITY_INSERT [dbo].[Teachers] ON 

INSERT [dbo].[Teachers] ([Id], [Name]) VALUES (1, N'Lic. Eduardo')
INSERT [dbo].[Teachers] ([Id], [Name]) VALUES (2, N'Lic. Marcela')
INSERT [dbo].[Teachers] ([Id], [Name]) VALUES (3, N'Lic. Luis')
INSERT [dbo].[Teachers] ([Id], [Name]) VALUES (4, N'Lic. Tatiana')
INSERT [dbo].[Teachers] ([Id], [Name]) VALUES (5, N'Lic. Oscar')
SET IDENTITY_INSERT [dbo].[Teachers] OFF
GO
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (1, 1)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (1, 2)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (2, 3)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (2, 4)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (3, 5)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (3, 6)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (4, 7)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (4, 8)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (5, 9)
INSERT [dbo].[TeacherSubject] ([TeacherId], [SubjectId]) VALUES (5, 10)
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([Id], [Username], [Password], [Role]) VALUES (1, N'admin', N'1234', N'admin')
INSERT [dbo].[Users] ([Id], [Username], [Password], [Role]) VALUES (2, N'student', N'0000', N'student')
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
/****** Object:  Index [IX_StudentSubject_SubjectId]    Script Date: 5/26/2025 8:17:37 AM ******/
CREATE NONCLUSTERED INDEX [IX_StudentSubject_SubjectId] ON [dbo].[StudentSubject]
(
	[SubjectId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, DROP_EXISTING = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
/****** Object:  Index [IX_TeacherSubject_SubjectId]    Script Date: 5/26/2025 8:17:37 AM ******/
CREATE NONCLUSTERED INDEX [IX_TeacherSubject_SubjectId] ON [dbo].[TeacherSubject]
(
	[SubjectId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, DROP_EXISTING = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Students] ADD  DEFAULT ((0)) FOR [rolestudent]
GO
ALTER TABLE [dbo].[Students] ADD  DEFAULT (N'') FOR [Password]
GO
ALTER TABLE [dbo].[StudentSubject] ADD  DEFAULT ((0)) FOR [TeacherId]
GO
ALTER TABLE [dbo].[StudentSubject]  WITH CHECK ADD  CONSTRAINT [FK_StudentSubject_Students_StudentId] FOREIGN KEY([StudentId])
REFERENCES [dbo].[Students] ([Id])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[StudentSubject] CHECK CONSTRAINT [FK_StudentSubject_Students_StudentId]
GO
ALTER TABLE [dbo].[StudentSubject]  WITH CHECK ADD  CONSTRAINT [FK_StudentSubject_Subjects_SubjectId] FOREIGN KEY([SubjectId])
REFERENCES [dbo].[Subjects] ([Id])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[StudentSubject] CHECK CONSTRAINT [FK_StudentSubject_Subjects_SubjectId]
GO
ALTER TABLE [dbo].[TeacherSubject]  WITH CHECK ADD  CONSTRAINT [FK_TeacherSubject_Subjects_SubjectId] FOREIGN KEY([SubjectId])
REFERENCES [dbo].[Subjects] ([Id])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[TeacherSubject] CHECK CONSTRAINT [FK_TeacherSubject_Subjects_SubjectId]
GO
ALTER TABLE [dbo].[TeacherSubject]  WITH CHECK ADD  CONSTRAINT [FK_TeacherSubject_Teachers_TeacherId] FOREIGN KEY([TeacherId])
REFERENCES [dbo].[Teachers] ([Id])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[TeacherSubject] CHECK CONSTRAINT [FK_TeacherSubject_Teachers_TeacherId]
GO
USE [master]
GO
ALTER DATABASE [UniversityPortalDB] SET  READ_WRITE 
GO
```



















## 📦 Requisitos Previos

- [.NET 7 SDK o superior](https://dotnet.microsoft.com/en-us/download)
- [Node.js y npm](https://nodejs.org/)
- [Angular CLI](https://angular.io/cli):
  
  ```bash
  npm install -g @angular/cli

🚀 Pasos para ejecutar el proyecto:

**1. Extraer archivos**
Descarga el .rar y extrae todos los archivos del proyecto en una carpeta local.

**2. Configurar la base de datos**
Antes de ejecutar el proyecto, configura la conexión a tu servidor SQL Server en el archivo appsettings.json.

Abre el archivo:
```
CD    "TuEquipo\EntregableInterRapidisimoAG\UniversityPortalTechnicalTestInterRapidisimo\UniversityPortal.PresentationniversityPortalAPI/appsettings.json"
```

Reemplaza la cadena de conexión por la tuya propia, por ejemplo:

En el caso de tener conexion 
WINDOWS AUTHENTICATION
```
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=UniversityPortalDB;Trusted_Connection=True;TrustServerCertificate=True;"
}
```
Para SQL AUTHENTICATION
```
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=UniversityPortalDB;User Id=tu_usuario;Password=tu_contraseña;TrustServerCertificate=True;"
}
```

**3. Cargar la Base de Datos**
Tienes dos opciones para cargar la base de datos:

**🔹 Opción 1: Cargar el script inicial manualmente**
Abre SQL Server Management Studio (SSMS) u otra herramienta compatible.

Ejecuta el script SQL inicial que se encuentra al inicio de este archivo README.

Esto creará las tablas y datos necesarios para comenzar.

🔹 Opción 2: Crear una **base de datos VACIA** mediante migraciones (Entity Framework Core)
Abre una consola dentro del proyecto de la API, en la carpeta de la capa de presentación.

Una vez en la ruta correcta, ejecuta los siguientes comandos:

```
dotnet restore
dotnet ef database update
```

Esto aplicará las migraciones existentes y generará una base de datos vacía con la estructura definida en el modelo.

Asegúrate de tener instalada la herramienta de Entity Framework Core CLI. Si no la tienes, instálala con este comando:

```
dotnet tool install --global dotnet-ef
```

**4. Ejecutar el backend (Web API)**
Ir la consola a la ubicacion correspondiente a la capa de presentacion:

```
CD   "TuEquipoLocal\EntregableInterRapidisimoAG\UniversityPortalTechnicalTestInterRapidisimo\UniversityPortal.PresentationniversityPortalAPI"
```

Luego inicia el proyecto.

```
dotnet run --urls "https://localhost:7228"
```

Esto levantará la API en:

```
https://localhost:7228/swagger/index.html
```

**5. Ejecutar el frontend (Angular)**
Abre una segunda consola y navega a la carpeta del frontend (UniversityPortalAngular). 

```
CD   "TuEquipoLocal\EntregableInterRapidisimoAG\UniversityPortalAngular"
```

Luego ejecuta:

```
npm install
ng serve -o
```

Esto abrirá automáticamente el navegador en: 

```
http://localhost:4200.
```

🧪 Pruebas
Puedes probar la API desde Swagger en:

```
https://localhost:7228/swagger/index.html
```

🛠️ Tecnologías utilizadas
.NET 8 (ASP.NET Core Web API)
Angular 19
SQL Server
Entity Framework Core
Bootstrap


📣 Notas
Asegúrate de que ninguna otra app esté usando el puerto 7228.

Este proyecto crea una base de datos vacía al ejecutar update-database. No contiene datos precargados.

📧 Autor
Anderson Gordillo
Correo: [mauri201111@gmail.com]

