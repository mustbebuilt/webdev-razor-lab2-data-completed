# Lab 2: Data & Databases in ASP.NET Core Razor Pages

[![.NET 10](https://img.shields.io/badge/.NET-10.0-512bd4.svg)](https://dotnet.microsoft.com/)
[![Razor Pages](https://img.shields.io/badge/ASP.NET%20Core-Razor%20Pages-0284c7.svg)](https://learn.microsoft.com/aspnet/core/razor-pages/)
[![SQLite](https://img.shields.io/badge/Database-SQLite-003B57.svg)](https://www.sqlite.org/)
[![EF Core](https://img.shields.io/badge/ORM-Entity%20Framework%20Core-68217a.svg)](https://learn.microsoft.com/ef/)

This is the **completed application** for Lab 2. It demonstrates an ASP.NET Core Razor Pages app that reads staff records from SQLite through Entity Framework Core (EF Core), searches records with LINQ, and displays individual staff details by route parameter.

> **Tutorial:** The step-by-step lab instructions are available in the [GitHub Wiki](https://github.com/mustbebuilt/webdev-razor-lab2-data/wiki).

## Requirements

- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- [Visual Studio Code](https://code.visualstudio.com/) or another editor (optional)
- SQLite CLI (optional, for inspecting the database or running SQL scripts)

Check the installed SDK:

```bash
dotnet --version
```

## Run the application

The repository includes the seeded SQLite database at `Data/staff.db`. From the project root, run:

```bash
dotnet run
```

Open the local URL printed by the application. The database connection is configured in `appsettings.json` and uses `Data/staff.db`.

To inspect the sample records with the SQLite CLI:

```bash
sqlite3 Data/staff.db "SELECT staff_id, first_name, last_name, department, salary, is_active FROM staff;"
```

The seed script for creating a fresh database is `resources/staff-sqlite.sql`. The application itself is configured for SQLite; `resources/staff-mssql.sql` is provided as a reference for the optional MSSQL tutorial.

## What the application demonstrates

- EF Core SQLite configuration and the `Staff` entity mapped to the `staff` table.
- A staff directory loaded asynchronously from the database.
- Search by first name or last name using an HTTP GET form and a deferred LINQ query.
- A staff details page addressed by integer route parameter (`/Staff/Details/{id}`).
- Display of staff contact, job, salary, and active-status information.

### Pages

| Page | Route | Description |
|---|---|---|
| Home | `/` | Overview and links to the completed lab features. |
| Staff Directory | `/Staff` | Search staff by first name or last name and open a staff record. |
| Staff Details | `/Staff/Details/{id}` | View an individual staff record. |
| News | `/News` | Lab announcement. |
| Privacy | `/Privacy` | Privacy information. |

## Sample data

The supplied SQLite database contains six sample staff records across Engineering, Human Resources, Finance, Marketing, and Sales. To inspect or recreate the schema and sample data, see [`resources/staff-sqlite.sql`](resources/staff-sqlite.sql).

## Repository structure

```text
├── Data/
│   ├── ApplicationDbContext.cs
│   └── staff.db
├── Models/
│   └── Staff.cs
├── Pages/
│   ├── Index.cshtml                 # Home page
│   └── Staff/
│       ├── Index.cshtml             # Searchable staff directory
│       └── Details.cshtml           # Individual staff record
├── resources/
│   ├── staff-sqlite.sql             # SQLite schema and sample data
│   └── staff-mssql.sql              # MSSQL alternative reference
└── wwwroot/
    ├── css/site.css
    └── js/site.js
```

## Lab topics

The [GitHub Wiki](https://github.com/mustbebuilt/webdev-razor-lab2-data/wiki) covers:

1. SQLite database integration with EF Core.
2. MSSQL database integration as an alternative.
3. Route parameters and a staff details page.
4. Searching data with LINQ and GET model binding.

For related demonstrations of HTTP methods and routing, see [webdev-razor-http-methods](https://github.com/mustbebuilt/webdev-razor-http-methods).

## License and attribution

Created for university and college Web Application Development modules. Free for educational use.
