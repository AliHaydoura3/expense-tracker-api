# Expense Tracker API

A RESTful API for tracking and managing personal expenses, with JWT-based authentication.

## Tech Stack

- ASP.NET Core Web API (.NET 9)
- Entity Framework Core with **PostgreSQL** (Npgsql)
- ASP.NET Identity + **JWT Bearer** authentication
- Swagger / OpenAPI
- MIT licensed

## Features

- Register and log in to get a JWT access token
- Create, list, update, and delete expenses (authenticated)
- Each expense stores an amount, description, category, and date
- Migrations included for the PostgreSQL schema

## Getting Started

### Prerequisites

- .NET 9 SDK
- PostgreSQL

### 1. Configuration

Provide the following settings via environment variables, user secrets, or `appsettings.json`:

| Setting                          | Description                              |
| -------------------------------- | ---------------------------------------- |
| `ConnectionStrings:DefaultConnection` | PostgreSQL connection string         |
| `Jwt:Issuer`                     | JWT issuer                               |
| `Jwt:Audience`                   | JWT audience                             |
| `Jwt:SecretKey`                  | Signing key for JWT tokens               |

> NOTE: `appsettings.Development.json` and other local secrets are not tracked in git.

### 2. Apply migrations

```bash
dotnet ef database update
```

### 3. Run

```bash
dotnet run
```

The API listens on the ports in `Properties/launchSettings.json`.

## API endpoints

| Method | Route                | Description                    |
| ------ | -------------------- | ------------------------------ |
| POST   | `/api/auth/register` | Register a new user            |
| POST   | `/api/auth/login`    | Log in and get a JWT token     |
| GET    | `/api/expenses`      | List the current user's expenses |
| GET    | `/api/expenses/{id}` | Get an expense by id           |
| POST   | `/api/expenses`      | Create an expense              |
| PUT    | `/api/expenses/{id}` | Update an expense              |
| DELETE | `/api/expenses/{id}` | Delete an expense              |

Send the JWT as a `Bearer` token in the `Authorization` header for the expense endpoints.

## Project Structure

```
Controllers/    API endpoints (Auth, Expenses)
Services/       Business logic and JWT generation
DTOs/           Request/response models
Models/         Entities (ApplicationUser, Expense)
Data/           EF Core DbContext
Migrations/     PostgreSQL schema migrations
```

## Author

Ali Haydoura