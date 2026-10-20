# How to Perform CRUD Operations on the ASP.NET Core Grid and Save to a Database

## Overview

This ASP.NET Core sample demonstrates how to wire the [Syncfusion ASP.NET Core Grid](https://ej2.syncfusion.com/aspnetcore/documentation/grid/getting-started-core) to a backend that loads and persists rows in SQL Server. The Grid is bound through the `UrlAdaptor` to controller actions that perform create, read, update, and delete operations against a SQL Server LocalDB database using Entity Framework Core. Server-side paging and sorting are handled in the controller via `DataManagerRequest`, so the Grid can scale beyond the size of a single page.

## Key Features

- Syncfusion ASP.NET Core Grid rendered with the `<ejs-grid>` Tag Helper from the `Syncfusion.EJ2.AspNet.Core` package.
- Remote data binding through `UrlAdaptor` configured on `<e-data-manager url="/DataGrid/UrlDataSource" adaptor="UrlAdaptor" insertUrl="/DataGrid/Insert" updateUrl="/DataGrid/Update" removeUrl="/DataGrid/Delete">`.
- Inline CRUD enabled by `<e-grid-editSettings allowAdding="true" allowDeleting="true" allowEditing="true" mode="Normal">` and the toolbar items `Add`, `Edit`, `Delete`, `Update`, `Cancel`.
- Server-side paging (`PerformSkip`, `PerformTake`) and sorting (`PerformSorting`) handled by `Syncfusion.EJ2.Base.DataOperations` inside `DataGridController.UrlDatasource`.
- Entity Framework Core persistence using `OrderDbContext : DbContext` over a `DbSet<Orders>` with `OrderID` (`[Key]`, identity, primary key) and `CustomerID`.
- SQL Server LocalDB persistence using the checked-in `WebApp/AppData/NORTHWND.MDF` database.
- Default route `{controller=DataGrid}/{action=Index}/{id?}` in `Startup.Configure` that opens the Grid on launch.

## Prerequisites

- Visual Studio 2022 or Visual Studio Code
- .NET SDK compatible with `netcoreapp2.1` (note: .NET Core 2.1 reached end of support on 2021-08-21; upgrade to a current LTS framework before production use)
- SQL Server Express LocalDB (the sample uses `(LocalDB)\MSSQLLocalDB` with `Integrated Security=True`)
- The NuGet packages `Microsoft.EntityFrameworkCore 2.1.14` and `Syncfusion.EJ2.AspNet.Core 17.3.0.28`, restored via `dotnet restore`

## How to Run the Project

### Visual Studio 2022

1. Clone or download this repository.
2. Open `WebApp.sln` in Visual Studio 2022.
3. Set `WebApp` as the startup project.
4. Restore NuGet packages (right-click the solution and choose **Restore NuGet Packages**, or run `dotnet restore` from the `WebApp` folder).
5. Update the SQL Server connection string in `WebApp/Models/OrderDbContext.cs` so `AttachDbFilename` points to the local `WebApp/AppData/NORTHWND.MDF` on your machine, or move the value to `WebApp/appsettings.json` and read it through configuration.
6. Press **F5** to build and run with the `WebApp` launch profile. Kestrel serves the app at `https://localhost:5001` and `http://localhost:5000` (IIS Express profile: `http://localhost:57852`).
7. The browser opens on `DataGrid/Index`. Verify that the Grid loads rows from `NORTHWND.MDF`, that paging and sorting work, and that Add, Edit, and Delete toolbar actions persist to the database.

### Visual Studio Code

1. Clone or download this repository.
2. Open the `WebApp` folder in Visual Studio Code.
3. Restore the NuGet packages:

   ```bash
   dotnet restore
   ```

4. Update the SQL Server connection string in `WebApp/Models/OrderDbContext.cs` so `AttachDbFilename` points to the local `WebApp/AppData/NORTHWND.MDF` on your machine, or move the value to `WebApp/appsettings.json`.
5. Build the project:

   ```bash
   dotnet build
   ```

6. Run the project:

   ```bash
   dotnet run
   ```

7. Open a browser at `https://localhost:5001` or `http://localhost:5000`. Verify that the Grid loads rows from `NORTHWND.MDF`, that paging and sorting work, and that Add, Edit, and Delete toolbar actions persist to the database.

## Project Structure

- `WebApp/WebApp.csproj` — project file targeting `netcoreapp2.1` with `Microsoft.EntityFrameworkCore` and `Syncfusion.EJ2.AspNet.Core` package references.
- `WebApp/Program.cs` — host entry point that loads `Startup`.
- `WebApp/Startup.cs` — services registration (`AddMvc`, `SetCompatibilityVersion(Version_2_1)`) and default route to `DataGrid/Index`.
- `WebApp/Controllers/DataGridController.cs` — `UrlDataSource`, `Insert`, `Update`, and `Delete` actions for the Syncfusion Grid `UrlAdaptor`.
- `WebApp/Controllers/HomeController.cs` — default MVC scaffold for the site layout.
- `WebApp/Models/Orders.cs` — `OrderID` (`[Key]`, primary key) and `CustomerID` entity.
- `WebApp/Models/OrderDbContext.cs` — EF Core `DbContext` with the SQL Server LocalDB connection string.
- `WebApp/Views/DataGrid/Index.cshtml` — Syncfusion Grid view using `<ejs-grid>`, `<e-data-manager>`, `<e-grid-editSettings>`, and `<e-grid-columns>` Tag Helpers.
- `WebApp/Views/Shared/_Layout.cshtml` — layout that loads Syncfusion scripts/styles from CDN and registers `<ejs-scripts>`.
- `WebApp/Properties/launchSettings.json` — Kestrel (`https://localhost:5001;http://localhost:5000`) and IIS Express (`http://localhost:57852`) launch profiles.
- `WebApp/AppData/NORTHWND.MDF` and `NORTHWND_log.ldf` — checked-in SQL Server LocalDB sample database.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Official documentation: [Syncfusion ASP.NET Core Grid Getting Started](https://ej2.syncfusion.com/aspnetcore/documentation/grid/getting-started-core)

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion products or components in your own applications.
