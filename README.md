# 🚀 DotNetCrud - ASP.NET Core CRUD Application

A simple and clean **ASP.NET Core MVC CRUD application** using **Entity Framework Core**. This project demonstrates how to perform basic database operations (Create, Read, Update, Delete) with a proper layered structure.

---

## 📌 Features

* ✅ Create, Read, Update, Delete (CRUD)
* ✅ Clean Architecture (MVC Pattern)
* ✅ Entity Framework Core Integration
* ✅ SQL Server Database
* ✅ Repository Pattern (optional if used)
* ✅ Simple and clean UI
* ✅ Scalable project structure

---

## 🛠️ Tech Stack

* **Backend:** ASP.NET Core MVC
* **Frontend:** Razor Views (HTML, CSS, Bootstrap)
* **Database:** SQL Server
* **ORM:** Entity Framework Core
* **Language:** C#
* **Tools:** Visual Studio / VS Code

---

## 📁 Project Structure

```
DotNetCrud/
│
├── Controllers/
│   └── ProductController.cs
│
├── Models/
│   └── Product.cs
│
├── Data/
│   └── AppDbContext.cs
│
├── Views/
│   └── Product/
│       ├── Index.cshtml
│       ├── Create.cshtml
│       ├── Edit.cshtml
│       └── Delete.cshtml
│
├── wwwroot/
│
├── appsettings.json
├── Program.cs
└── Startup.cs (if applicable)
```

---

## ⚙️ Prerequisites

Before running the project, make sure you have:

* .NET SDK (6 or later)
* SQL Server
* Visual Studio / VS Code
* Git installed

---

## 📥 Clone the Repository

```bash
git clone https://github.com/your-username/DotNetCrud.git
cd DotNetCrud
```

---

## 🔧 Configure Connection String

Open **appsettings.json** and update your database connection:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER;Database=DotNetCrudDb;Trusted_Connection=True;"
}
```

---

## 🧱 Add Migration & Create Database

Run the following commands:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

---

## ▶️ Run the Application

```bash
dotnet run
```

Then open in browser:

```
https://localhost:5001
```

---

## 🗄️ Database Schema (Overview)

### Product Table

| Column Name | Data Type | Description    |
| ----------- | --------- | -------------- |
| Id          | int (PK)  | Primary Key    |
| Name        | nvarchar  | Product Name   |
| Price       | decimal   | Product Price  |
| Quantity    | int       | Stock Quantity |

---

## 📚 EF Core Command Reference

| Command                         | Description           |
| ------------------------------- | --------------------- |
| `dotnet ef migrations add Name` | Add new migration     |
| `dotnet ef database update`     | Apply migration       |
| `dotnet ef migrations remove`   | Remove last migration |
| `dotnet ef database drop`       | Delete database       |

---

## 💻 Sample Code

### Model

```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
    public int Quantity { get; set; }
}
```

---

### DbContext

```csharp
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options) { }

    public DbSet<Product> Products { get; set; }
}
```

---

### Controller (Basic CRUD Example)

```csharp
public class ProductController : Controller
{
    private readonly AppDbContext _context;

    public ProductController(AppDbContext context)
    {
        _context = context;
    }

    public IActionResult Index()
    {
        return View(_context.Products.ToList());
    }

    public IActionResult Create()
    {
        return View();
    }

    [HttpPost]
    public IActionResult Create(Product product)
    {
        _context.Products.Add(product);
        _context.SaveChanges();
        return RedirectToAction("Index");
    }
}
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new branch (`feature/new-feature`)
3. Commit your changes
4. Push to your branch
5. Open a Pull Request

---

## 👨‍💻 Author

**Asim**
📧 Email: [asimaly12144@gmail.com](mailto:asimaly12144@gmail.com)
🔗 GitHub: https://github.com/asimaly12144-coder

---

## ⭐ Support

If you like this project, give it a ⭐ on GitHub!

---
