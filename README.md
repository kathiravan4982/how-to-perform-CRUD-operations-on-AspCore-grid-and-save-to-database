# How to Perform CRUD Operations on the ASP.NET Core Grid and Save to a Database

## Project Overview

This sample shows how the [Syncfusion EJ2 ASP.NET Core Data Grid](https://www.syncfusion.com/aspnet-core-ui-controls/grid) integrates with an ASP.NET Core backend using the URL adaptor. Grid data is retrieved from and saved to a SQL Server database through MVC controller actions implemented with Entity Framework Core.

The application uses a local NORTHWND database and focuses on practical server-side data handling such as create, read, update, delete, paging, and sorting operations.

## Key Features

- Uses the Syncfusion EJ2 ASP.NET Core `DataGrid` to display order records from SQL Server.
- Uses `UrlAdaptor` to communicate with server-side controller actions.
- Supports adding, editing, and deleting order records directly from the Data Grid.
- Saves Data Grid changes to the SQL Server database.
- Uses Entity Framework Core with `OrderDbContext` for database operations.
- Processes Data Grid queries and CRUD requests using the Syncfusion `DataManager`.

## Prerequisites

- Visual Studio 2022 or Visual Studio Code
- .NET SDK compatible with the project's target framework
- SQL Server LocalDB or Express

## Running the Application

### Visual Studio 2022

1. Clone or download this repository.
2. Open the solution file:

   `WebApp.sln`

3. Update the SQL Server database connection string used by `OrderDbContext` with the server name, database name, and authentication details for a database that you are authorized to access.
4. Restore the NuGet packages by rebuilding the solution.
5. Set the startup project to:

   `WebApp`

6. Build the solution.
7. Run the application using `Ctrl+F5`.
8. Open the application URL displayed by Visual Studio after launch.
9. Verify that the Data Grid displays order records from SQL Server and that adding, editing, or deleting a record saves the changes to the database.

### Visual Studio Code

1. Clone or download this repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory:

```bash
cd WebApp
```

5. Update the SQL Server database connection string used by `OrderDbContext` with the server name, database name, and authentication details for a database that you are authorized to access.
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
10. Verify that the Data Grid displays order records from SQL Server and that adding, editing, or deleting a record saves the changes to the database.

## Project Structure

- `WebApp/Controllers/DataGridController.cs` — handles Data Grid requests and performs the server-side read, insert, update, and delete operations.
- `WebApp/Models/OrderDbContext.cs` — defines the Entity Framework Core database context used to access order records.
- `WebApp/Models/Orders.cs` — defines the order model displayed and managed by the Data Grid.
- `WebApp/Views/DataGrid/Index.cshtml` — configures and renders the Syncfusion EJ2 ASP.NET Core Data Grid with the URL adaptor.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Official documentation: [Getting Started with ASP.NET Core DataGrid](https://help.syncfusion.com/grid-sdk/asp-net-core/data-grid/getting-started-core)

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.