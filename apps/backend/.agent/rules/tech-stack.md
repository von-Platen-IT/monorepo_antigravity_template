# Backend Tech Stack & Guidelines (.NET 9)

**Scope:** `apps/backend/` ONLY. Ignoriere alle Frontend-Regeln für app/web, wenn du hier arbeitest.

## 1. Core Stack
- **Framework:** .NET 9 (ASP.NET Core Web API).
- **Sprache:** C# 13 (Nutze Primary Constructors, Collection Expressions).
- **Datenbank:** PostgreSQL.
- **ORM:** Entity Framework Core 9 (`Npgsql.EntityFrameworkCore.PostgreSQL`).

## 2. Architektur & Paradigmen
- [MUST] Nutze Minimal APIs (`app.MapGet()`, `app.MapPost()`) oder das Endpoint-Pattern. Vermeide schwere `ControllerBase`-Klassen.
- [NEVER] erstelle eine `Startup.cs`. Die gesamte Konfiguration findet in der `Program.cs` (Top-Level Statements) statt.
- [MUST] Nutze strikt Dependency Injection (DI) für alle Services.

## 3. Entity Framework Core (PostgreSQL)
- [NEVER] schreibe rohes SQL oder ändere Tabellen manuell. Nutze IMMER Code-First Migrations (`dotnet ef migrations add`).
- Nutze für alle DB-Abfragen durchgehend asynchrone Methoden (`async/await`, z.B. `ToListAsync()`).

## 4. API & Error Handling
- Gebe [NEVER] unformatierte Exceptions an den Client zurück. Nutze die native `.NET 9 ProblemDetails` Implementierung.
- Jeder API-Endpunkt [MUST] saubere HTTP-Statuscodes (200, 201, 400, 404) zurückgeben.
