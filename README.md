# UniversityPortal - Proyecto Full Stack (.NET Web API + Angular)

Este proyecto es una aplicación web educativa construida con **ASP.NET Core Web API** y **Angular**. Permite visualizar estudiantes, materias y sus relaciones.


## Script para Portal Universitario
```sql
SELECT * FROM Clientes WHERE Activo = 1;
```

## 📦 Requisitos Previos

- [.NET 7 SDK o superior](https://dotnet.microsoft.com/en-us/download)
- [Node.js y npm](https://nodejs.org/)
- [Angular CLI](https://angular.io/cli):  
  ```bash
  npm install -g @angular/cli

🚀 Pasos para ejecutar el proyecto
1. Extraer archivos
Descarga el .rar y extrae todos los archivos del proyecto en una carpeta local.

2. Configurar la base de datos
Antes de ejecutar el proyecto, configura la conexión a tu servidor SQL Server.

Abre el archivo:
"Maquina Local"\EntregableInterRapidisimoAG\UniversityPortalTechnicalTestInterRapidisimo\UniversityPortal.PresentationniversityPortalAPI/appsettings.json

Reemplaza la cadena de conexión por la tuya propia, por ejemplo:

En el caso de tener conexion WINDOWS AUTHENTICATION
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=UniversityPortalDB;Trusted_Connection=True;TrustServerCertificate=True;"
}

pendiente para cuando es SQL AUTHENTICATION

3. Crear la base de datos (estructura vacía)
Abre una consola dentro del proyecto de la API, el cual deberia ejecutarse en la carpeta de la capa de presentacion como se observa en la imagen.
![image](https://github.com/user-attachments/assets/8f03cfa0-f65d-4398-a9a9-2377337626c6)
cuando se encuentre dentro de la ruta, ejecuta:
dotnet restore
dotnet ef database update
Esto aplicará las migraciones y creará la base de datos vacía.

Asegúrate de tener instalada la herramienta de Entity Framework Core CLI:
dotnet tool install --global dotnet-ef


4. Ejecutar el backend (Web API)
Desde la misma consola:
dotnet run --urls "https://localhost:7228"
Esto levantará la API en:
https://localhost:7228/swagger/index.html

5. Ejecutar el frontend (Angular)
Abre una segunda consola y navega a la carpeta del frontend (UniversityPortalAngular). Luego ejecuta:
npm install
ng serve -o
Esto abrirá automáticamente el navegador en http://localhost:4200.

Agregar usuario ADMIN mediante SWAGGER para tener acceso al portal universitario en la siguiente ruta
https://localhost:7228/swagger/index.html
tal como aparece en la imagen, ingresar a la peticion POST api/student.
![image](https://github.com/user-attachments/assets/33ddbac5-7148-40c5-b50e-c351408e0960)
ingresa el usuario ADMIN de la siguiente manera y asi ya tienes tu usuario para controlar el portal.
![image](https://github.com/user-attachments/assets/7bb48654-c837-4f37-8dfd-880fbaf9d3ea)



🧪 Pruebas
Puedes probar la API desde Swagger en:
https://localhost:7228/swagger/index.html

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

