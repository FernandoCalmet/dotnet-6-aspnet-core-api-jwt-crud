# 馃 C# ASPNET Core 6 API CRUD JWT

[![Github][github-shield]][github-url]
[![Kofi][kofi-shield]][kofi-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
[![Khanakat][khanakat-shield]][khanakat-url]

## TABLA DE CONTENIDO

* [Acerca del proyecto](#acerca-del-proyecto)
* [Instalaci贸n](#instalaci贸n)
* [Resumen Te贸rico](#resumen-te贸rico)
  * [Permitir atributo an贸nimo .NET](#permitir-atributo-an%C3%B3nimo-net)
  * [Atributo de autorizaci贸n personalizado de .NET](#atributo-de-autorizaci%C3%B3n-personalizado-de-net)
  * [Middleware de JWT personalizado de .NET](#middleware-de-jwt-personalizado-de-net)
  * [Utilidades de .NET JWT](#utilidades-de-net-jwt)
  * [Controlador de usuarios de .NET](#controlador-de-usuarios-de-net)
  * [Entidad de usuario de .NET](#entidad-de-usuario-de-net)
  * [Excepci贸n de aplicaci贸n personalizada de .NET](#excepci%C3%B3n-de-aplicaci%C3%B3n-personalizada-de-net)
  * [Configuraci贸n de la aplicaci贸n .NET](#configuraci%C3%B3n-de-la-aplicaci%C3%B3n-net)
  * [Perfil de .NET AutoMapper](#perfil-de-net-automapper)
  * [Contexto de datos .NET](#contexto-de-datos-net)
  * [Middleware del controlador de errores globales .NET](#middleware-del-controlador-de-errores-globales-net)
  * [Contexto de datos SQLite de .NET](#contexto-de-datos-sqlite-de-net)
  * [Migraciones de EF Core SQLite](#migraciones-de-ef-core-sqlite)
  * [Migraciones de EF Core SQL Server](#migraciones-de-ef-core-sql-server)
  * [Modelo de solicitud de autenticaci贸n de .NET](#modelo-de-solicitud-de-autenticaci%C3%B3n-de-net)
  * [Modelo de respuesta de autenticaci贸n de .NET](#modelo-de-respuesta-de-autenticaci%C3%B3n-de-net)
  * [Modelo de solicitud de registro](#modelo-de-solicitud-de-registro)
  * [Modelo de solicitud de actualizaci贸n](#modelo-de-solicitud-de-actualizaci%C3%B3n)
  * [Configuraci贸n de lanzamiento de .NET.json](#configuraci%C3%B3n-de-lanzamiento-de-netjson)
  * [Servicio de usuario .NET](#servicio-de-usuario-net)
  * [Configuraci贸n de la aplicaci贸n .NET 6 (Desarrollo)](#configuraci%C3%B3n-de-la-aplicaci%C3%B3n-net-6-desarrollo)
  * [Configuraci贸n de la aplicaci贸n .NET 6](#configuraci%C3%B3n-de-la-aplicaci%C3%B3n-net-6)
  * [Configuraci贸n OmniSharp](#configuraci%C3%B3n-omnisharp)
  * [Programa .NET 6](#programa-net-6)
  * [.NET 6 API web csproj](#net-6-api-web-csproj)
* [Despliegue en Azure](#despliegue-en-azure)
  * [Crear un nuevo servidor de Windows en Microsoft Azure](#crear-un-nuevo-servidor-de-windows-en-microsoft-azure)
  * [Conectarse a la instancia de Azure Windows Server a trav茅s de RDP](#conectarse-a-la-instancia-de-azure-windows-server-a-trav%C3%A9s-de-rdp)
  * [Configuraci贸n del servidor web con IIS (Servicios de informaci贸n de Internet)](#configuraci%C3%B3n-del-servidor-web-con-iis-servicios-de-informaci%C3%B3n-de-internet)
  * [Crear base de datos Azure SQL](#crear-base-de-datos-azure-sql)
  * [Crear e implementar la API back-end de ASP.NET Core en Azure](#crear-e-implementar-la-api-back-end-de-aspnet-core-en-azure)
  * [Crear e implementar la aplicaci贸n front-end de Angular en Azure](#crear-e-implementar-la-aplicaci%C3%B3n-front-end-de-angular-en-azure)
  * [Configurar IIS para servir el front-end de Angular y la API de ASP.NET Core](#configurar-iis-para-servir-el-front-end-de-angular-y-la-api-de-aspnet-core)
  * [Prueba de la aplicaci贸n Angular + ASP.NET Core + SQL Server ejecut谩ndose en Azure](#prueba-de-la-aplicaci%C3%B3n-angular--aspnet-core--sql-server-ejecut%C3%A1ndose-en-azure)
* [Dependencias](#dependencias)
* [Licencia](#licencia)

## 馃敟 ACERCA DEL PROYECTO

馃 Este proyecto es una muestra de una soluci贸n CRUD base de una API con autenticaci贸n JWT. Se utilizo ``ASP.NET Core 6`` Web API.

## 鉁旓笍 CARACTER脥STICAS

- [x] JWT Authentication
- [x] Authenticate User
- [x] Register User
- [x] Get All Users
- [x] Get User by ID
- [x] Update User
- [x] Delete User

## 鈿欙笍 INSTALACI脫N

Clonar el repositorio.

```bash
gh repo clone FernandoCalmet/dotnet-6-aspnet-core-api-jwt-crud
```

Crear migraci贸n de base de datos.

```bash
cd .\MinimalCRUDWebAPI
```

SQL Server EF Core Migrations (Windows Command): `RECOMENDADA`

```bash
set ASPNETCORE_ENVIRONMENT=Production
dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations
```

SQLite EF Core Migrations (Windows/MacOS): `ALTERNATIVA`

```bash
dotnet ef migrations add InitialCreate --context SqliteDataContext --output-dir Migrations/SqliteMigrations
```

SQL Server EF Core Migrations (Windows PowerShell): `ALTERNATIVA`
```bash
$env:ASPNETCORE_ENVIRONMENT="Production"
dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations
```

SQL Server EF Core Migrations (MacOS): `ALTERNATIVA`
```bash
ASPNETCORE_ENVIRONMENT=Production dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations
```

Migrar a base de datos

```bash
dotnet ef database update --context MinimalCRUDWebAPI.Helpers.DataContext
```

### OTROS COMANDOS

Instalar Herramienta DOTNET por la consola del administrador de paquetes.

```bash
dotnet tool install --global dotnet-ef
```

Verificar Herramienta DOTNET por la consola del administrador de paquetes.

```bash
dotnet ef
```

Crear migracion de base de datos

```bash
dotnet ef migrations add Initial
```

Migrar base de datos

```bash
dotnet ef database update
```

### EJECUTAR

Ejecutar aplicaci贸n por consola.

```bash
dotnet run
```

## 馃摀 RESUMEN TE脫RICO

### Permitir atributo an贸nimo .NET

Ruta: `/Authorization/AllowAnonymousAttribute.cs`  
El atributo `[AllowAnonymous]` personalizado se usa para permitir el acceso an贸nimo a m茅todos de acci贸n espec铆ficos de controladores que est谩n decorados con el atributo `[Authorize]`. Se utiliza en el controlador de usuarios para permitir el acceso an贸nimo a los m茅todos de acci贸n de registro e inicio de sesi贸n. El atributo de autorizaci贸n personalizado a continuaci贸n omite la autorizaci贸n si el m茅todo de acci贸n est谩 decorado con `[AllowAnonymous]`.

Cre茅 un permiso an贸nimo personalizado (en lugar de usar el integrado) para mantener la coherencia y evitar errores de referencia ambiguos entre espacios de nombres.

### Atributo de autorizaci贸n personalizado de .NET

Ruta: `/Authorization/AuthorizeAttribute.cs`  
El atributo `[Authorize]` personalizado se usa para restringir el acceso a controladores o m茅todos de acci贸n espec铆ficos. Solo las solicitudes autorizadas pueden acceder a los m茅todos de acci贸n que est谩n decorados con el atributo `[Authorize]`.

Cuando un controlador est谩 decorado con el atributo `[Authorize]`, todos los m茅todos de acci贸n est谩n restringidos a solicitudes autorizadas, excepto los m茅todos decorados con el atributo `[AllowAnonymous]` personalizado anterior.

La autorizaci贸n se realiza mediante el OnAuthorizationm茅todo que verifica si hay un usuario autenticado adjunto a la solicitud actual ( context.HttpContext.Items["User"]). El middleware jwt personalizado adjunta un usuario autenticado si la solicitud contiene un token de acceso JWT v谩lido.

### Middleware de JWT personalizado de .NET

Ruta: `/Authorization/JwtMiddleware.cs`  
El middleware JWT personalizado extrae el token JWT del Authorizationencabezado de la solicitud (si lo hay) y lo valida con el jwtUtils.ValidateToken()m茅todo. Si la validaci贸n es exitosa, se devuelve la identificaci贸n de usuario del token y el objeto de usuario autenticado se adjunta a la HttpContext.Itemscolecci贸n para que sea accesible dentro del alcance de la solicitud actual.

Si la validaci贸n del token falla o no hay ning煤n token, la solicitud es an贸nima y solo se le permite acceder a las rutas p煤blicas porque no hay un objeto de usuario autenticado adjunto al contexto HTTP. La l贸gica de autorizaci贸n que comprueba que el objeto de usuario est谩 adjunto se encuentra en el atributo de autorizaci贸n personalizado . Si se env铆a una solicitud an贸nima a una ruta segura, 401 Unauthorizedel atributo de autorizaci贸n devuelve una respuesta.

### Utilidades de .NET JWT

Ruta: `/Authorization/JwtUtils.cs`  
La clase utils de JWT contiene m茅todos para generar y validar tokens de JWT.

El m茅todo `GenerateToken()` genera un token JWT con la identificaci贸n del `user` especificado como "id" de reclamo, lo que significa que la carga 煤til del token contendr谩 la propiedad `"id"`: <userId>(p. ej "id": 1., ).

El ValidateToken()m茅todo intenta validar el token JWT proporcionado y devolver la identificaci贸n de usuario (`"id"`) de las notificaciones del token. Si la validaci贸n falla, se devuelve nulo.

### Controlador de usuarios de .NET

Ruta: `/Controllers/UsersController.cs`  
El controlador de usuarios de .NET define y maneja todas las rutas/puntos finales para la API que se relacionan con los usuarios, esto incluye autenticaci贸n, registro y operaciones CRUD est谩ndar. Dentro de cada ruta, el controlador llama al servicio de usuario para realizar la acci贸n requerida, lo que mantiene al controlador "esbelto" y completamente separado de la base de datos/c贸digo de persistencia.

Los m茅todos de acci贸n del controlador son seguros de forma predeterminada con el atributo `[Authorize]` personalizado en la clase, los m茅todos Authenticatey Registerpermiten el acceso p煤blico anulando el atributo `[Authorize]` en el controlador con un atributo `[AllowAnonymous]` en cada m茅todo de acci贸n. Eleg铆 este enfoque por seguridad para evitar que una ruta se haga p煤blica accidentalmente, cualquier m茅todo de acci贸n nuevo ser谩 seguro de forma predeterminada a menos que se haga p煤blico expl铆citamente.

### Entidad de usuario de .NET

Ruta: `/Entidades/Usuario.cs`  
La clase de entidad de usuario representa los datos almacenados en la base de datos para los usuarios.

Las clases de entidad tambi茅n se usan para pasar datos entre diferentes partes de la aplicaci贸n (p. ej., entre servicios y controladores) y se pueden usar para devolver datos de respuesta http desde los m茅todos de acci贸n del controlador.

El atributo `[JsonIgnore]` evita que la propiedad `PasswordHash` se serialice y se devuelva en las respuestas de API.

### Excepci贸n de aplicaci贸n personalizada de .NET

Ruta: `/Helpers/AppException.cs`  
La excepci贸n de aplicaci贸n es una clase de excepci贸n personalizada que se usa para diferenciar entre excepciones controladas y no controladas en la API de .NET. Las excepciones controladas son generadas por el c贸digo de la aplicaci贸n y se utilizan para devolver mensajes de error amigables, por ejemplo, excepciones de validaci贸n o l贸gica de negocios causadas por par谩metros de solicitud no v谩lidos, mientras que las excepciones no controladas son generadas por el marco .NET o causadas por errores en el c贸digo de la aplicaci贸n.

Las excepciones son manejadas en el ejemplo por el middleware del controlador de errores global , y algunas excepciones de aplicaciones son lanzadas por el servicio de usuario cuando falla la validaci贸n.

### Configuraci贸n de la aplicaci贸n .NET

Ruta: `/Helpers/AppSettings.cs`  
La clase de configuraci贸n de la aplicaci贸n contiene propiedades definidas en el archivo appsettings.json y se usa para acceder a la configuraci贸n de la aplicaci贸n a trav茅s de objetos que se inyectan en clases mediante el sistema de inyecci贸n de dependencia (DI) de .NET 6.0. Por ejemplo, el `controlador de usuarios` accede a la configuraci贸n de la aplicaci贸n a trav茅s de un objeto `IOptions<AppSettings> appSettings` que se inyecta en su constructor.

### Perfil de .NET AutoMapper

Ruta: `/Helpers/AutoMapperProfile.cs`  
El perfil de automapper contiene la configuraci贸n de mapeo utilizada por la aplicaci贸n, AutoMapper es un paquete disponible en Nuget que permite el mapeo autom谩tico de un tipo de clase a otro. En este ejemplo, lo estamos usando para mapear entre la entidad `User` y algunos tipos de modelos diferentes: `AuthenticateResponse`, `RegisterRequesty` y `UpdateRequest`.

Todos los perfiles de automapper en el proyecto se ejecutan al inicio con una llamada `services.AddAutoMapper(typeof(Program))` en el archivo de programa .NET . El par谩metro de tipo `typeof(Program)` le dice a automapper que busque todos los perfiles de automapper en el ensamblaje del proyecto actual, cualquier tipo en el proyecto podr铆a usarse ya que es simplemente un tipo de marcador para el ensamblaje.

### Contexto de datos .NET

Ruta: `/Helpers/DataContext.cs`  
El contexto de datos se usa para acceder a los datos de la aplicaci贸n a trav茅s de Entity Framework Core y est谩 configurado para conectarse a una base de datos de SQL Server. Se deriva de la clase EF Core `DbContext` y tiene una propiedad `Users` p煤blica para acceder y administrar datos de usuario. El contexto de datos es utilizado por el `servicio de usuario` para manejar todas las operaciones de datos de bajo nivel.

En entornos de desarrollo, la API est谩 configurada para usar el `contexto de datos SQLite` que hereda `DataContexty` anula el proveedor de base de datos para conectarse a una base de datos SQLite local en lugar de SQL Server.

### Middleware del controlador de errores globales .NET

Ruta: `/Helpers/ErrorHandlerMiddleware.cs`  
El controlador de errores global se utiliza para capturar todos los errores y eliminar la necesidad de duplicar el c贸digo de manejo de errores en toda la API de .NET 6. Est谩 configurado como middleware en el archivo `Program.cs`.

Los errores de tipo `AppExceptionse` tratan como errores personalizados (espec铆ficos de la aplicaci贸n) que devuelven una respuesta `400 Bad Request`, la clase integrada de .NET `KeyNotFoundExceptionse` usa para devolver respuestas `404 Not Found`, todas las dem谩s excepciones no se controlan y devuelven una respuesta `500 Internal Server Error`.

Consulte el servicio de atenci贸n al usuario para ver ejemplos de errores personalizados y errores no encontrados generados por la API.

### Contexto de datos SQLite de .NET

Ruta: `/Helpers/SqliteDataContext.cs`  
La API utiliza el contexto de datos de SQLite en entornos de desarrollo, se hereda del `contexto de datos` principal y reemplaza al proveedor para usar SQLite en lugar de SQL Server.

### Migraciones de EF Core SQLite

Ruta: `/Migrations/SqliteMigraciones`  
Migraciones de Entity Framework Core para el proveedor de base de datos SQLite utilizado en entornos de desarrollo.

Las migraciones de este ejemplo se generaron con el comando `dotnet ef migrations add InitialCreate --context SqliteDataContext --output-dir Migrations/SqliteMigrations`.

Las migraciones se generan para SQLite porque la clase `SqliteDataContext` est谩 configurada para conectarse a una base de datos SQLite. `SqliteDataContext` Hereda de la clase principal y `DataContext` reemplaza al proveedor para usar SQLite en lugar de SQL Server. Esto permite que el proyecto admita m煤ltiples proveedores de bases de datos diferentes para diferentes entornos.

Para instalar las herramientas de EF Core para la CLI de .NET, ejecute globalmente `dotnet tool install -g dotnet-ef`, o para actualizar, ejecute `dotnet tool update -g dotnet-ef`.

### Migraciones de EF Core SQL Server

Ruta: `/Migrations/SqlServerMigrations`  
Migraciones de Entity Framework Core para el proveedor de base de datos de SQL Server utilizado en entornos de producci贸n.

Las migraciones en este ejemplo se generaron con el siguiente comando.

Comando de Windows: Windows PowerShell: MacOS:
`set ASPNETCORE_ENVIRONMENT=Production`
`dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations`

`$env:ASPNETCORE_ENVIRONMENT="Production"`
`dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations`

`ASPNETCORE_ENVIRONMENT=Production dotnet ef migrations add InitialCreate --context DataContext --output-dir Migrations/SqlServerMigrations`

La variable de entorno `ASPNETCORE_ENVIRONMENT` debe establecerse en `Production` para que la clase de SQL Server `DataContext` se configure con el sistema de inserci贸n de dependencias de .NET; consulte el c贸digo de configuraci贸n del contexto de datos en el archivo `del programa de .NET`.

Para instalar las herramientas de EF Core para la CLI de .NET, ejecute globalmente `dotnet tool install -g dotnet-ef`, o para actualizar, ejecute `dotnet tool update -g dotnet-ef`.

### Modelo de solicitud de autenticaci贸n de .NET

Ruta: `/Models/Users/AuthenticateRequest.cs`  
El modelo de solicitud de autenticaci贸n define los par谩metros para las solicitudes POST entrantes a la ruta `/users/authenticate`, se adjunta a la ruta configur谩ndolo como el par谩metro del m茅todo `Authenticate` de acci贸n del controlador de usuarios . Cuando la ruta recibe una solicitud HTTP POST, los datos del cuerpo se vinculan a una instancia de la clase `AuthenticateRequest`, se validan y se pasan al m茅todo.

Las anotaciones de datos .NET se utilizan para manejar autom谩ticamente la validaci贸n del modelo, el atributo `[Required]` establece el nombre de usuario y la contrase帽a como campos obligatorios, por lo que si falta alguno, la API devuelve un mensaje de error de validaci贸n.

### Modelo de respuesta de autenticaci贸n de .NET

Ruta: `/Models/Users/AuthenticateResponse.cs`  
El modelo de respuesta de autenticaci贸n define los datos devueltos por el m茅todo `Authenticate` del `controlador de usuarios`. Incluye detalles b谩sicos de usuario y un `token JWT`.

### Modelo de solicitud de registro

Ruta: `/Models/Users/RegisterRequest.cs`  
El modelo de solicitud de registro define los par谩metros para las solicitudes POST entrantes a la ruta `/users/register`, se adjunta a la ruta al configurarlo como par谩metro para el Registerm茅todo de acci贸n del `controlador de usuarios`. Cuando la ruta recibe una solicitud HTTP POST, los datos del cuerpo se vinculan a una instancia de la clase `RegisterRequest`, se validan y se pasan al m茅todo.

Las anotaciones de datos .NET se utilizan para manejar autom谩ticamente la validaci贸n del modelo, el atributo `[Required]` establece todos los campos como obligatorios, de modo que si falta alguno, la API devuelve un mensaje de error de validaci贸n.

### Modelo de solicitud de actualizaci贸n

Ruta: `/Models/Users/UpdateRequest.cs`  
El modelo de solicitud de actualizaci贸n define los par谩metros para las solicitudes PUT entrantes a la ruta `/users/{id}`, se adjunta a la ruta al configurarlo como el par谩metro del Updatem茅todo de acci贸n del controlador de usuarios . Cuando la ruta recibe una solicitud HTTP PUT, los datos del cuerpo se vinculan a una instancia de la clase `UpdateRequest`, se validan y se pasan al m茅todo.

Ninguna de las propiedades tiene el atributo `[Required]`, por lo que todas son opcionales. Los campos omitidos se ignoran cuando se actualiza un usuario, la configuraci贸n para esto se encuentra en el mapeo `UpdateRequest -> User`  del `perfil del automapeador`.

### Configuraci贸n de lanzamiento de .NET.json

Ruta: `/Properties/launchSettings.json`  
Archivo de configuraci贸n que contiene configuraciones y perfiles de inicio utilizados al iniciar la aplicaci贸n en su m谩quina local. El primer perfil del archivo ( Desarrollo ) se usa de forma predeterminada al iniciar la aplicaci贸n con `dotnet run`, el archivo puede contener varios perfiles y se puede especificar un perfil de inicio diferente con el argumento de la l铆nea de comandos `--launch-profile "PROFILE_NAME"`.

El archivo launchSettings.json no se implementa, solo se usa en su m谩quina de desarrollo local. Para obtener m谩s informaci贸n, consulte https://docs.microsoft.com/aspnet/core/fundamentals/environments?view=aspnetcore-6.0#lsj .

### Servicio de usuario .NET

Ruta: `/Services/UserService.cs`  
El servicio de usuario es responsable de toda la interacci贸n de la base de datos y la l贸gica comercial central relacionada con el inicio de sesi贸n, el registro y las operaciones CRUD del usuario.

La parte superior del archivo contiene una interfaz que define el servicio de usuario, justo debajo est谩 la clase de servicio de usuario concreta que implementa la interfaz. BCrypt se utiliza para codificar y verificar contrase帽as; para obtener m谩s informaci贸n, consulte .NET 6.0 - `Hash` y `verificaci贸n de contrase帽as` con `BCrypt`.

### Configuraci贸n de la aplicaci贸n .NET 6 (Desarrollo)

Ruta: `/appsettings.Development.json`  
Archivo de configuraci贸n con ajustes de la aplicaci贸n que son espec铆ficos del entorno de desarrollo, incluye la cadena de conexi贸n `WebApiDatabase` para la base de datos de desarrollo de SQLite local que anula la cadena de conexi贸n en el archivo base `appsettings.json`.

### Configuraci贸n de la aplicaci贸n .NET 6

Ruta: `/appsettings.json`  
Archivo de configuraci贸n base que contiene la configuraci贸n predeterminada de la aplicaci贸n para todos los entornos (a menos que se anule en la configuraci贸n espec铆fica del entorno). Incluye marcador de posici贸n para su cadena de conexi贸n de SQL Server de producci贸n.

IMPORTANTE: `"Secret"` la API utiliza la propiedad para firmar y verificar los tokens JWT para la autenticaci贸n, actual铆cela con su propia cadena aleatoria para asegurarse de que nadie m谩s pueda generar un JWT para obtener acceso no autorizado a su aplicaci贸n. Una forma r谩pida y f谩cil es unir un par de GUID para crear una cadena aleatoria larga (por ejemplo, de https://www.guidgenerator.com/ ).

### Configuraci贸n OmniSharp

Ruta: `/omnisharp.json`  
Este archivo contiene opciones de configuraci贸n para la extensi贸n de C# en VS Code. La opci贸n `useBundledOnly` le dice a la extensi贸n de C# que use la versi贸n integrada de MSBuild en lugar de la versi贸n global para evitar errores si tiene una versi贸n anterior de MSBuild instalada globalmente (por ejemplo, como parte de Visual Studio).

### Programa .NET 6

Ruta: `/Programa.cs`  
El archivo de programa .NET 6 contiene declaraciones de nivel superior que el nuevo compilador C# 10 convierte en un m茅todo `Main()`  y una Programclase para el programa .NET. El m茅todo `Main()` es el punto de entrada para una aplicaci贸n .NET, cuando se inicia una aplicaci贸n busca el m茅todo `Main()` para comenzar la ejecuci贸n. Las declaraciones de nivel superior se pueden ubicar en cualquier parte del proyecto, pero generalmente se colocan en el archivo `Program.cs`; solo un archivo puede contener declaraciones de nivel superior dentro de una aplicaci贸n .NET.

La clase `WebApplication` maneja el inicio de la aplicaci贸n, la administraci贸n de por vida, la configuraci贸n del servidor web y m谩s. `WebApplicationBuilder` se crea primero llamando al m茅todo est谩tico `WebApplication.CreateBuilder(args)`, el constructor se usa para configurar servicios para inyecci贸n de dependencia (DI), `WebApplicationse` crea una instancia llamando `builder.Build()`, la instancia de la aplicaci贸n se usa para configurar la canalizaci贸n de solicitud HTTP (middleware), luego la aplicaci贸n es empez贸 llamando `app.Run()`.

Envolv铆 las secciones agregar servicios... y configurar HTTP... entre corchetes `{}` para agruparlos visualmente, los corchetes son completamente opcionales.

Internamente, la clase `WebApplicationBuilder` llama al m茅todo `ConfigureWebHostDefaults()` de extensi贸n que configura el alojamiento para la aplicaci贸n web, incluida la configuraci贸n de Kestrel como servidor web, la adici贸n de middleware de filtrado de host y la habilitaci贸n de la integraci贸n de IIS. Para obtener m谩s informaci贸n sobre la configuraci贸n predeterminada del generador, consulte https://docs.microsoft.com/aspnet/core/fundamentals/host/generic-host#default-builder-settings .

### .NET 6 API web csproj

Ruta: `/WebApi.csproj`  
El csproj (proyecto C#) es un archivo basado en MSBuild que contiene el marco de destino y la informaci贸n de dependencia del paquete NuGet para la aplicaci贸n. La funci贸n `ImplicitUsings` est谩 habilitada, lo que le dice al compilador que genere autom谩ticamente un conjunto de directivas de uso globales basadas en el tipo de proyecto, lo que elimina la necesidad de incluir muchas declaraciones de uso comunes. Las instrucciones de uso globales se generan autom谩ticamente cuando crea el proyecto y se pueden encontrar en el archivo `/obj/Debug/net6.0/WebApi.GlobalUsings.g.cs`.

Para obtener m谩s informaci贸n sobre el archivo de proyecto de C#, consulte .NET + MSBuild - Archivo de proyecto de C# (.csproj) en pocas palabras .

## DESPLIEGUE EN AZURE

### Crear un nuevo servidor de Windows en Microsoft Azure

Antes de hacer nada, necesitamos un servidor en el que podamos trabajar, siga estos pasos para activar una nueva instancia de Windows Server 2019 utilizando el servicio Azure Virtual Machines.

1. Inicie sesi贸n en Azure Portal en https://portal.azure.com/ . Si a煤n no tiene una cuenta de Azure, puede crear una gratuita en https://azure.microsoft.com/free .

2. Vaya a la secci贸n de servicio de M谩quinas Virtuales.

3. Haga clic en "Agregar" para crear una nueva m谩quina virtual.

4. Lo esencial
- **Grupo de recursos** : haga clic en "Crear nuevo" e ingrese un nombre para el grupo de recursos (por ejemplo, mi grupo de recursos).
- **Nombre de la m谩quina virtual** : ingrese un nombre para la m谩quina virtual (por ejemplo, mi servidor).
- **Imagen** : seleccione "Windows Server 2019 Datacenter".
- **Tama帽o** : haga clic en "Cambiar tama帽o", seleccione "B1ms" y haga clic en el bot贸n "Seleccionar". Esta m谩quina virtual tiene 2 GB de RAM, que es aproximadamente el m铆nimo que desea ejecutar para Windows Server.
- **Nombre de usuario** : ingrese el nombre de usuario del administrador para el servidor.
- **Contrase帽a** : ingrese la contrase帽a de administrador para el servidor.
- **Confirmar contrase帽a** : vuelva a ingresar la contrase帽a de administrador para el servidor.
- **Seleccione los puertos entrantes** : permita el tr谩fico "HTTP (80)" y "RDP (3389)" a trav茅s del servidor.

5. **Gesti贸n** : establezca la supervisi贸n de diagn贸sticos de arranque en "Desactivado".

6. **Revisar + crear** : haz clic en "Crear".

### Conectarse a la instancia de Azure Windows Server a trav茅s de RDP

Una vez que la VM de Azure Windows Server est茅 lista, puede conectarse a ella a trav茅s de RDP (Protocolo de escritorio remoto). Si est谩 en Windows, debe tener un cliente RDP instalado de forma predeterminada, si est谩 en Mac OSX, puede instalar un cliente RDP desde la tienda de aplicaciones aqu铆 .

1. Cuando finalice la implementaci贸n, haga clic en "Ir al recurso" para acceder a la p谩gina de descripci贸n general de la m谩quina virtual de Azure.

2. En la p谩gina de descripci贸n general de Azure Virtual Machine, haga clic en "Conectar".

3. Haga clic en "Descargar archivo RDP".

4. Abra el archivo RDP descargado. Si ve un mensaje que indica que no se puede identificar al editor, haga clic en "Conectar".

5. Ingrese el nombre de usuario y la contrase帽a del paso anterior y haga clic en "Aceptar". Si ve un mensaje que indica que no se puede identificar la identidad de la computadora remota, haga clic en "S铆", esta advertencia es solo porque es un certificado SSL autofirmado y no hay nada de qu茅 preocuparse.

### Configuraci贸n del servidor web con IIS (Servicios de informaci贸n de Internet)

Cuando se conecte por primera vez a la instancia de Azure Windows Server a trav茅s de RDP, deber铆a ver la interfaz del Administrador del servidor.

1. **Administrador del servidor**
- Haga clic en "Agregar roles y caracter铆sticas".
- **Tipo de instalaci贸n** : seleccione "Instalaci贸n basada en funciones o funciones" y haga clic en Siguiente.
- **Selecci贸n de servidor** : deje el valor predeterminado y haga clic en Siguiente.
- **Funciones del servidor** : marque la casilla "Servidor web (IIS)", luego haga clic en el bot贸n "Agregar caracter铆sticas" en la ventana emergente y haga clic en Siguiente.
- **Funciones** : deje el valor predeterminado y haga clic en Siguiente.
- **Rol de servidor web (IIS)** : deje el valor predeterminado y haga clic en Siguiente.
- **Servicios de funci贸n** : deje los valores predeterminados y haga clic en Siguiente.
- **Confirmaci贸n** - Haga clic en instalar.
- **Resultados** : espere a que se complete la instalaci贸n y haga clic en cerrar.

2. Descargue e instale el paquete de alojamiento de .NET Core desde https://www.microsoft.com/net/permalink/dotnetcore-current-windows-runtime-bundle-installer . Haga esto descargando el archivo a su m谩quina local y copi谩ndolo en el servidor a trav茅s del escritorio remoto, o agregando `https://*.microsoft.com` a los "Sitios confiables" en la configuraci贸n de seguridad de Internet Explorer en el servidor para permitir que el archivo se descargue.

3. Reinicie IIS con el comando `net stop was /y && net start w3svc`

4. Descargue e instale el m贸dulo de reescritura de URL de IIS desde https://www.iis.net/downloads/microsoft/url-rewrite . Haga esto descargando el archivo a su m谩quina local y copi谩ndolo al servidor a trav茅s del escritorio remoto, o agregando `https://www.iis.net` y `https://webpihandler.azurewebsites.net` a los "Sitios confiables" en la configuraci贸n de seguridad de Internet Explorer en el servidor para permitir que el archivo se descargue.

### Crear base de datos Azure SQL

A continuaci贸n, crearemos una nueva base de datos de SQL Server para la aplicaci贸n en la nube mediante el servicio Azure SQL Database.

1. Vaya a la secci贸n **Bases de datos SQL** del portal de Azure, puede encontrar esto ingresando "SQL" en la barra de b煤squeda principal y seleccionando el servicio "Bases de datos SQL".

2. Haga clic en "Agregar" o "Crear base de datos SQL".

3. **Lo esencial**
- **Grupo de recursos** : seleccione el mismo grupo de recursos en el que se encuentra la m谩quina virtual de Windows Server (por ejemplo, mi grupo de recursos).
- **Nombre de la base de datos** : ingrese un nombre para la base de datos SQL (por ejemplo, my-sql-db).
- **Servidor** : haga clic en "Crear nuevo".
  - Nombre del servidor : ingrese un nombre 煤nico global para el servidor, se usar谩 para crear la URL del servidor Azure SQL: `<server-name>.database.windows.net.`
  - **Inicio de sesi贸n del administrador del servidor** : ingrese el nombre de usuario del administrador para el servidor Azure SQL.
  - **Contrase帽a** : ingrese la contrase帽a de administrador para el servidor Azure SQL.
  - **Confirmar contrase帽a** : vuelva a ingresar la contrase帽a de administrador para el servidor Azure SQL.
  - **Ubicaci贸n** : seleccione la misma regi贸n que la m谩quina virtual de Windows Server.
- **C贸mputo + almacenamiento** : haga clic en "Configurar base de datos", luego seleccione "B谩sico" y haga clic en el bot贸n "Aplicar".

4. **Redes**
- M茅todo de conectividad : seleccione "Punto final p煤blico".
- Permitir que los servicios y recursos de Azure accedan a este servidor : seleccione "S铆".

5. **Revisar + crear** : haz clic en "Crear".

### Crear e implementar la API back-end de ASP.NET Core en Azure

Siga estos pasos para clonar y compilar la API ASP.NET Core en su m谩quina local y luego implementarla en el servidor.

1. Clonar el proyecto ASP.NET Core API en una carpeta en su m谩quina local con el comando git clone `https://github.com/FernandoCalmet/DOTNET-6-ASPNET-Core-API-JWT-CRUD.git`. Si no tiene instalada la CLI de Git, puede descargarla desde https://git-scm.com/downloads . El proyecto de back-end tiene como nombre `CRUDWebAPI`.

2. Actualice la cadena de conexi贸n de la base de datos para que apunte a la nueva base de datos SQL de Azure:
- En Azure Portal, vaya a la p谩gina de descripci贸n general de la base de datos SQL creada en el paso anterior.
- Haga clic en "Mostrar cadenas de conexi贸n de la base de datos" y copie la cadena de conexi贸n "ADO.NET (autenticaci贸n SQL)".
- Abra el archivo de configuraci贸n de la aplicaci贸n ASP.NET Core (`/appsettings.json`) en un editor de texto.
- Reemplace el valor de la `DefaultConnection` cadena de conexi贸n con el que acaba de copiar, para que se vea as铆:

```
"ConnectionStrings": {
  "DefaultConnection": "Server=tcp:{server_name},1433;Initial Catalog={database_name};Persist Security Info=False;User ID={user_name};Password={your_password};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"
},
```

- Dentro de la cadena de conexi贸n, reempl谩cela `{your_password}` con la contrase帽a de administrador del servidor Azure SQL que cre贸 al configurar la base de datos.

3. Actualice el secreto de firma del token JWT:
- Abra el archivo de configuraci贸n de la aplicaci贸n ASP.NET Core (`/appsettings.json`) en un editor de texto.
- Reemplace el valor de la configuraci贸n de la aplicaci贸n `Secret` con su propia cadena aleatoria, una forma r谩pida y f谩cil es generar un par de GUID y unirlos para crear una cadena aleatoria larga (por ejemplo, de https://www.guidgenerator.com/ ).

4. Cree la API con el comando `dotnet publish --configuration Release` desde la carpeta ra铆z del proyecto (donde se encuentra el archivo WebApi.csproj). Si no tiene instalado .NET Core SDK, puede descargarlo desde https://www.microsoft.com/net/download/core .

5. Copie los archivos del directorio `aspnet-core-3-registration-login-api\bin\Release\netcoreapp3.1\publish` al directorio `C:\Projects\back-end` en el servidor a trav茅s del escritorio remoto.
  
Los archivos de la API de ASP.NET Core ahora est谩n implementados en el servidor, pero la API a煤n no est谩 en funcionamiento; esto suceder谩 cuando configuremos IIS en breve.

### Crear e implementar la aplicaci贸n front-end de Angular en Azure

Siga estos pasos para compilar la aplicaci贸n Angular en su m谩quina local y luego implementarla en el servidor de Azure.

1. Clone el proyecto Angular a una carpeta en su m谩quina local con el comando git clone `https://github.com/FernandoCalmet/DOTNET-6-ASPNET-Core-API-JWT-CRUD.git`. Si no tiene instalada la CLI de Git, puede descargarla desde https://git-scm.com/downloads .El proyecto de back-end tiene como nombre `WebFrontEnd`.

2. Navegue al directorio clonado e instale todos los paquetes de nodos requeridos con el comando `npm install`. Si necesita instalar Node.js (que incluye npm), puede descargarlo desde https://nodejs.org/ .

3. Cree la aplicaci贸n Angular con el comando `npm run build`.

4. Copie los archivos del directorio `angular-8-registration-login-crud\dist` al directorio `C:\Projects\front-end` en el servidor a trav茅s del escritorio remoto.

### Configurar IIS para servir el front-end de Angular y la API de ASP.NET Core

ado que nuestra aplicaci贸n Angular + ASP.NET Core se compone de dos proyectos separados a los que se debe acceder a trav茅s del mismo puerto (HTTP en el puerto 80), vamos a configurar un solo sitio en IIS para atender el frente de Angular. finalice la aplicaci贸n desde la ruta base ( /) y cree una aplicaci贸n secundaria para ASP.NET Core API que maneje todas las solicitudes que comiencen con la ruta /api.

Siga estos pasos para configurar IIS para la aplicaci贸n de pila completa Angular + ASP.NET Core.

1. Abra IIS en el servidor.
2. Elimine el "Sitio web predeterminado" en Sitios y "DefaultAppPool" en Grupos de aplicaciones.
3. Haga clic derecho en la carpeta Sitios y seleccione "Agregar sitio web".
4. Ingrese el nombre del sitio (por ejemplo, mi aplicaci贸n).
5. Establezca la ruta f铆sica al directorio de la aplicaci贸n Angular (`C:\Projects\front-end`).
6. Deje el nombre de host vac铆o y haga clic en "Aceptar".
7. Haga clic derecho en el nuevo sitio y seleccione "Agregar aplicaci贸n".
8. Introduzca el alias "api" (sin comillas).
9. Establezca la ruta f铆sica al directorio api de ASP.NET Core (`C:\Projects\back-end`).
10. Haga clic en Aceptar".
11. En Grupos de aplicaciones, haga clic con el bot贸n derecho en el grupo de aplicaciones para el nuevo sitio y seleccione "Configuraci贸n b谩sica". Cambie la versi贸n de .NET CLR a 'Sin c贸digo administrado', las aplicaciones .NET Core no requieren .NET CLR.
12. Cree un archivo llamado "web.config" dentro de la carpeta front-end de Angular (`C:\Projects\front-end`) y agregue la siguiente configuraci贸n:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.webServer>
        <staticContent>
            <remove fileExtension=".js" />
            <mimeMap fileExtension=".js" mimeType="application/javascript; charset=UTF-8" />
        </staticContent>
        <rewrite>
            <rules>
                <rule name="Angular" stopProcessing="true">
                    <match url=".*" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_URI}" pattern="^/api/.*" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="/" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

La configuraci贸n `<staticContent>` establece la codificaci贸n de caracteres en "UTF-8" para los archivos javascript, lo que evita que los caracteres Unicode en su javascript se conviertan antes de enviarse al navegador, lo que puede causar errores (por ejemplo, errores de expresi贸n regular no v谩lidos).

La configuraci贸n `<rewrite>` crea una regla de reescritura que permite actualizar la aplicaci贸n Angular sin obtener errores 404.

### Pruebar la aplicaci贸n Angular + ASP.NET Core + SQL Server ejecut谩ndose en Azure

ngrese la direcci贸n IP p煤blica de su Azure Windows Server en un navegador para acceder y probar su nueva aplicaci贸n de pila completa Angular + ASP.NET Core + Azure SQL Server.

La direcci贸n IP p煤blica se puede ubicar en la p谩gina de descripci贸n general de la m谩quina virtual en el portal de Microsoft Azure.

## 馃摜 DEPENDENCIAS

- [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) : Herramientas Swagger para documentar API creadas en ASP.NET Core.
- [Microsoft.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/) : Entity Framework Core es un moderno mapeador de bases de datos de objetos para .NET. Admite consultas LINQ, seguimiento de cambios, actualizaciones y migraciones de esquemas. EF Core funciona con SQL Server, Azure SQL Database, SQLite, Azure Cosmos DB, MySQL, PostgreSQL y otras bases de datos a trav茅s de una API de complemento de proveedor.
- [Microsoft.EntityFrameworkCore.Design](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Design/) : Proveedor de base de datos de Microsoft SQL Server para Entity Framework Core.
- [Microsoft.EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer/) : Componentes de tiempo de dise帽o compartidos para las herramientas de Entity Framework Core.
- [Microsoft.EntityFrameworkCore.Sqlite](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/) : Proveedor de base de datos SQLite para Entity Framework Core.
- [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer/) : Middleware ASP.NET Core que permite que una aplicaci贸n reciba un token de portador de OpenID Connect.
- [AutoMapper](https://www.nuget.org/packages/AutoMapper/) : AutoMapper es una peque帽a biblioteca simple creada para resolver un problema aparentemente complejo: deshacerse del c贸digo que mape贸 un objeto a otro. Este tipo de c贸digo es bastante triste y aburrido de escribir, entonces, 驴por qu茅 no inventar una herramienta que lo haga por nosotros?
- [AutoMapper.Extensions.Microsoft.DependencyInjection](https://www.nuget.org/packages/AutoMapper.Extensions.Microsoft.DependencyInjection/) : Extensi贸nes para AutoMapper ASP.NET Core.
- [BCrypt.Net-Next](https://www.nuget.org/packages/BCrypt.Net-Next/) : Segmentaci贸n de NET 6.
- [System.IdentityModel.Tokens.Jwt](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/) : Incluye tipos que brindan soporte para crear, serializar y validar tokens web JSON.

## 馃搫 LICENCIA

Este proyecto est谩 bajo la Licencia (Licencia MIT) - mire el archivo [LICENSE](LICENSE) para m谩s detalles.

## 猸愶笍 DAME UNA ESTRELLA

Si esta Implementaci贸n le result贸 煤til o la utiliz贸 en sus Proyectos, d茅le una estrella. 隆Gracias! O, si te sientes realmente generoso, [隆Apoye el proyecto con una peque帽a contribuci贸n!](https://ko-fi.com/fernandocalmet).

<!--- reference style links --->
[github-shield]: https://img.shields.io/badge/-@fernandocalmet-%23181717?style=flat-square&logo=github
[github-url]: https://github.com/fernandocalmet
[kofi-shield]: https://img.shields.io/badge/-@fernandocalmet-%231DA1F2?style=flat-square&logo=kofi&logoColor=ff5f5f
[kofi-url]: https://ko-fi.com/fernandocalmet
[linkedin-shield]: https://img.shields.io/badge/-fernandocalmet-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/fernandocalmet
[linkedin-url]: https://www.linkedin.com/in/fernandocalmet
[khanakat-shield]: https://img.shields.io/badge/khanakat.com-brightgreen?style=flat-square
[khanakat-url]: https://khanakat.com
