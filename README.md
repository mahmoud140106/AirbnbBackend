# Airbnb Backend Clone - Clean Architecture

![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-8.0-512bd4)
![Architecture](https://img.shields.io/badge/Architecture-Clean%20Architecture-blue)
![Database](https://img.shields.io/badge/Database-SQL%20Server-red)
![Real-time](https://img.shields.io/badge/Real--time-SignalR-orange)
![Payments](https://img.shields.io/badge/Payments-Stripe-6772e5)

A robust and scalable backend for an Airbnb-style web application, built using **ASP.NET Core** and following **Clean Architecture** principles.

## 🏗️ Architecture Overview

The project is structured into four main layers to ensure separation of concerns and maintainability:

1.  **Domain (Core)**: Contains enterprise-level entities, enums, and domain logic. It has no dependencies on any other architectural layer.
2.  **Application**: Defines business logic, service interfaces, DTOs, mappings, and result patterns. This layer orchestrates the flow of data.
3.  **Infrastructure**: Handles external concerns such as data persistence (EF Core, Repositories), external service integrations (Stripe, AI services), and file systems.
4.  **Presentation (Airbnb Web API)**: The entry point of the application, responsible for handling HTTP requests, middlewares, SignalR hubs, and providing the API endpoints.

---

## 🚀 Key Features

- **User Management**: Authentication and Authorization using ASP.NET Core Identity and JWT (stored in cookies).
- **Property Management**: Complete CRUD for property listings, amenities, and property types.
- **Booking & Reservations**: Complex reservation logic with calendar availability tracking.
- **Real-time Chat**: Instance messaging between hosts and guests powered by **SignalR**.
- **AI ChatBot**: Integrated **Groq AI** for handling automated guest inquiries.
- **Payment Integration**: Secure payment processing via **Stripe API**.
- **Notifications**: Real-time updates for bookings and messages using SignalR hubs.
- **Reviews & Ratings**: Systematic review system for properties with host reply capabilities.
- **Wishlist**: Allows users to save their favorite properties for later.
- **Security & Performance**:
  - IP Rate Limiting.
  - JWT Token validation middleware.
  - Environment variable management via `.env`.
  - AutoMapper for efficient DTO mapping.

---

## 🛠️ Technologies Used

- **Framework**: .NET 8.0 (ASP.NET Core Web API)
- **Database**: Entity Framework Core with SQL Server
- **Authentication**: JWT & ASP.NET Identity
- **Real-time**: SignalR
- **External APIs**: Stripe (Payments), Groq (AI)
- **Utilities**: AutoMapper, DotNetEnv, AspNetCoreRateLimit

---

## 📂 Project Structure

```bash
├── Airbnb (Presentation Layer)
│   ├── Controllers
│   ├── Hubs (SignalR)
│   ├── Middlewares
│   └── DependencyInjection
├── Application (Business Logic)
│   ├── Services
│   ├── Interfaces
│   ├── DTOs
│   └── Mappings (AutoMapper)
├── Domain (Enterprise Logic)
│   ├── Models (Entities)
│   └── Enums
└── Infrastructure (External Concerns)
    ├── Contexts (EF Core)
    ├── Repositories
    ├── DbConfigs
    └── DbSeeders
```

---

## 🛫 Getting Started

### Prerequisites

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

### Setup

1. Clone the repository.
2. Create a `.env` file in the `Airbnb` folder with the following variables:
   ```env
   STRIPE_SECRET_KEY=your_stripe_key
   GROQ_API_KEY=your_groq_key
   CONNECTION_STRING=your_db_connection_string
   ```
3. Run migrations and update the database:
   ```bash
   dotnet ef database update --project Infrastructure --startup-project Airbnb
   ```
4. Start the application:
   ```bash
   dotnet run --project Airbnb
   ```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
