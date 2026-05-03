# 🚀 DotNetCrud - ASP.NET Core Web API

A clean and scalable **ASP.NET Core Web API** project for performing CRUD operations using **Entity Framework Core**. This project follows RESTful principles and is suitable for frontend integration (React, Angular, etc.).

---

## 📌 Features

* ✅ RESTful API (GET, POST, PUT, DELETE)
* ✅ Entity Framework Core Integration
* ✅ SQL Server Database
* ✅ Clean layered structure
* ✅ JSON-based communication
* ✅ Swagger UI for testing APIs

---

## 🛠️ Tech Stack

* **Backend:** ASP.NET Core Web API
* **Database:** SQL Server
* **ORM:** Entity Framework Core
* **Language:** C#
* **Tools:** Visual Studio / VS Code / Swagger

---

## 📁 Project Structure

```id="1j9s7k"
DotNetCrudApi/
│
├── Controllers/
│   └── ProductsController.cs
│
├── Models/
│   └── Product.cs
│
├── Data/
│   └── AppDbContext.cs
│
├── DTOs/ (Optional but recommended)
│   └── ProductDto.cs
│
├── appsettings.json
├── Program.cs
```

---

## ⚙️ Prerequisites

* .NET SDK (6 or later)
* SQL Server
* Visual Studio / VS Code
* Git

---

## 📥 Clone the Repository

```bash id="x3kgdl"
git clone https://github.com/your-username/DotNetCrudApi.git
cd DotNetCrudApi
```

---

## 🔧 Configure Connection String

```json id="9m7m2l"
"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER;Database=DotNetCrudDb;Trusted_Connection=True;"
}
```

---

## 🧱 Add Migration & Create Database

```bash id="9r2bqs"
dotnet ef migrations add InitialCreate
dotnet ef database update
```

---

## ▶️ Run the Application

```bash id="v7m1hz"
dotnet run
```

Open Swagger UI:

```id="p0k9f1"
https://localhost:5001/swagger
```

---

## 🗄️ Database Schema (Overview)

### Product Table

| Column Name | Data Type | Description   |
| ----------- | --------- | ------------- |
| Id          | int (PK)  | Primary Key   |
| Name        | string    | Product Name  |
| Price       | decimal   | Product Price |
| Quantity    | int       | Stock         |

---

## 📚 EF Core Command Reference

| Command                         | Description           |
| ------------------------------- | --------------------- |
| `dotnet ef migrations add Name` | Add migration         |
| `dotnet ef database update`     | Apply migration       |
| `dotnet ef migrations remove`   | Remove last migration |
| `dotnet ef database drop`       | Delete DB             |

---

## 💻 Sample Code

### 📌 Model

```csharp id="g2k1xm"
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
    public int Quantity { get; set; }
}
```

---

### 📌 DbContext

```csharp id="w8p4zl"
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options) { }

    public DbSet<Product> Products { get; set; }
}
```

---

### 📌 Controller (Web API)

```csharp id="m1z8ap"
[Route("api/[controller]")]
[ApiController]
public class ProductsController : ControllerBase
{
    private readonly AppDbContext _context;

    public ProductsController(AppDbContext context)
    {
        _context = context;
    }

    // GET: api/products
    [HttpGet]
    public IActionResult GetAll()
    {
        var products = _context.Products.ToList();
        return Ok(products);
    }

    // GET: api/products/5
    [HttpGet("{id}")]
    public IActionResult GetById(int id)
    {
        var product = _context.Products.Find(id);
        if (product == null)
            return NotFound();

        return Ok(product);
    }

    // POST: api/products
    [HttpPost]
    public IActionResult Create(Product product)
    {
        _context.Products.Add(product);
        _context.SaveChanges();
        return Ok(product);
    }

    // PUT: api/products/5
    [HttpPut("{id}")]
    public IActionResult Update(int id, Product product)
    {
        if (id != product.Id)
            return BadRequest();

        _context.Products.Update(product);
        _context.SaveChanges();
        return NoContent();
    }

    // DELETE: api/products/5
    [HttpDelete("{id}")]
    public IActionResult Delete(int id)
    {
        var product = _context.Products.Find(id);
        if (product == null)
            return NotFound();

        _context.Products.Remove(product);
        _context.SaveChanges();
        return NoContent();
    }
}
```

---

## 🔍 API Endpoints

| Method | Endpoint             | Description        |
| ------ | -------------------- | ------------------ |
| GET    | `/api/products`      | Get all products   |
| GET    | `/api/products/{id}` | Get product by ID  |
| POST   | `/api/products`      | Create new product |
| PUT    | `/api/products/{id}` | Update product     |
| DELETE | `/api/products/{id}` | Delete product     |

---

## 🤝 Contributing

1. Fork the repository
2. Create a branch (`feature/api-improvement`)
3. Commit changes
4. Push to GitHub
5. Create Pull Request

---

## 👨‍💻 Author

**Aasim**
📧 [asimaly12144@gmail.com](mailto:asimaly12144@gmail.com)
🔗 https://github.com/asimaly12144-coder

---

## ⭐ Support

If you like this project, give it a ⭐ on GitHub!

---
