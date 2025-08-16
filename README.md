# Smart Inventory Management System

A microservices-based system to manage products, process orders, and notify on low stock.  
**Tech:** ASP.NET Core Web API, Azure SQL Database, Azure Functions.

## Architecture
- **Product Service (ASP.NET Core)** — CRUD for products.
- **Order Service (ASP.NET Core)** — accepts orders and updates product inventory.
- **Low Stock Notifier (Azure Functions, Timer + HTTP)** — hourly check for products with `QuantityInStock < Threshold`, plus an HTTP manual trigger.

![Architecture](./docs/architecture-diagram.png)

## Tech Stack
- **Backend:** .NET 8 (ASP.NET Core Web API)
- **Database:** Azure SQL Database (or local SQL Server for dev)
- **Serverless:** Azure Functions (Timer + HTTP)
- **Hosting:** Azure App Service (APIs), Azure Functions

## API Endpoints (Samples)
**Product Service**
- `POST /api/products`
- `GET /api/products`
- `GET /api/products/{id}`
- `PUT /api/products/{id}`
- `DELETE /api/products/{id}`

**Order Service**
- `POST /api/orders`
- `GET /api/orders`

**Low Stock Notifier**
- Timer trigger: hourly (`0 0 * * * *`)
- HTTP trigger: `GET /api/check-stock-now`

## License
MIT
