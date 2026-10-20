# How to Perform CRUD Operations on the ASP.NET Core Grid and Save to a Database

## Overview

This sample demonstrates how to perform create, read, update, and delete operations on the Syncfusion ASP.NET Core Grid and persist the changes to a database. The application connects the Grid to server-side controller actions through the URL adaptor, which uses Entity Framework Core to load and persist rows in a SQL Server database. It provides a browser-based interface for managing order records stored in the configured database.

## Key Features

- Uses the Syncfusion EJ2 ASP.NET Core `Grid` (`<ejs-grid>` Tag Helper) to display and edit order records.
- Binds the Grid through the URL adaptor with `url`, `insertUrl`, `updateUrl`, and `removeUrl` configured on `<e-data-manager adaptor="UrlAdaptor">`.
- Enables inline CRUD through `<e-grid-editSettings allowAdding="true" allowDeleting="true" allowEditing="true" mode="Normal">`.
- Provides the toolbar items `Add`, `Edit`, `Delete`, `Update`, and `Cancel` for row-level operations.
- Performs server-side paging and sorting in `DataGridController.UrlDatasource` using `PerformSkip`, `PerformTake`, and `PerformSorting` from `Syncfusion.EJ2.Base.DataOperations`.
- Persists changes through `OrderDbContext : DbContext` using `Microsoft.EntityFrameworkCore`.
- Reads and writes rows from the checked-in SQL Server LocalDB database `WebApp/AppData/NORTHWND.MDF`.
- Opens the Grid on launch through the default route `{controller=DataGrid}/{action=Index}/{id?}` declared in `Startup.Configure`.

## Prerequisites

- Visual Studio 2022 or Visual Studio Code
- .NET SDK compatible with the project's target framework (`netcoreapp2.1`)
- SQL Server Express LocalDB with access to a valid `NORTHWND` database file

## How to Run the Project

### Visual Studio 2022

1. Clone or download this repository.
2. Open the solution file:

   `WebApp.sln`

3. Ensure that the SQL Server LocalDB configuration in `Models/OrderDbContext.cs` points to a `NORTHWND.MDF` instance that you are authorized to access.
4. Restore the NuGet packages by rebuilding the solution.
5. Set the startup project to:

   `WebApp`

6. Build the solution.
7. Run the application using `Ctrl+F5`.
8. Open the application URL displayed by Visual Studio after launch.
9. Verify that the Grid displays rows from the configured database and that Add, Edit, and Delete operations persist to the database.

### Visual Studio Code

1. Clone or download this repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory:

```bash
cd WebApp
```

5. Ensure that the SQL Server LocalDB configuration in `Models/OrderDbContext.cs` points to a `NORTHWND.MDF` instance that you are authorized to access.
6. Restore the NuGet packages:

```bash
dotnet restore
```

7. Build the project:

```bash
dotnet build
```

8. Run the project:

```bash
dotnet run
```

9. Open the local URL displayed in the terminal after the application starts.
10. Verify that the Grid displays rows from the configured database and that Add, Edit, and Delete operations persist to the database.

## Project Structure

- `WebApp/Controllers/DataGridController.cs` — handles Grid requests, exposes `UrlDataSource`, `Insert`, `Update`, and `Delete` actions, and performs server-side paging and sorting.
- `WebApp/Models/OrderDbContext.cs` — EF Core `DbContext` that defines the `Orders` entity set and the SQL Server LocalDB connection string.
- `WebApp/Models/Orders.cs` — entity definition for `OrderID` and `CustomerID`.
- `WebApp/Views/DataGrid/Index.cshtml` — renders the Syncfusion EJ2 Grid bound to the URL adaptor with inline editing, paging, and sorting.
- `WebApp/Views/Shared/_Layout.cshtml` — layout that loads Syncfusion scripts and styles from CDN and registers `<ejs-scripts>`.
- `WebApp/Startup.cs` — services registration and default route to the Grid view.
- `WebApp/AppData/NORTHWND.MDF` — checked-in SQL Server LocalDB sample database.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Official documentation: [Getting Started with ASP.NET Core Grid](https://ej2.syncfusion.com/aspnetcore/documentation/grid/getting-started-core)

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.
