# Employee Management System

## Overview

This is a comprehensive ASP.NET Core Web API project demonstrating enterprise-level unit testing practices and architecture patterns. The solution manages employee information, including internal employees, external employees, employee promotions, and company statistics.

## Project Structure

### Core Projects

- **EmployeeManagement**: Main ASP.NET Core Web API application that handles employee management operations
- **EmployeeManagement.Test**: Comprehensive test suite covering controllers, services, middleware, and business logic
- **CompanyFramework**: Shared framework library for common company-wide utilities
- **CompanyFramework.Test**: Unit tests for the framework library
- **TopLevelManagement**: Secondary API service for top-level management operations

## Key Features

### Employee Management
- **Internal Employees**: Create, retrieve, update, and manage internal employees
- **External Employees**: Support for external/contractor employee records
- **Employee Data**: Track employee information including names, salaries, tenure, and performance metrics

### Promotions
- **Promotion Eligibility**: Determine which employees are eligible for promotion
- **Promotion Tracking**: Record and manage employee promotions
- **Promotion Services**: Business logic for evaluating and processing promotions

### Additional Features
- **Statistics**: Generate and retrieve company employee statistics
- **Course Management**: Track employee course attendance
- **Security Headers Middleware**: Custom middleware for adding security headers to HTTP responses
- **Auto Mapping**: Uses AutoMapper for DTO-to-entity conversions

## Architecture

### Layered Architecture

1. **Controllers** (`Controllers/`): API endpoints for HTTP requests
   - `InternalEmployeesController`: Employee CRUD operations
   - `PromotionsController`: Promotion management
   - `StatisticsController`: Statistics generation
   - `DemoInternalEmployeesController`: Demo/testing endpoints

2. **Business Logic** (`Business/`): Core application logic
   - `IEmployeeService` / `EmployeeService`: Employee operations
   - `IPromotionService` / `PromotionService`: Promotion handling
   - `EmployeeFactory`: Factory pattern for employee creation
   - `PromotionEligibility`: Eligibility determination logic

3. **Data Access** (`DataAccess/`): Database operations
   - Entity Framework Core DbContext
   - Repository pattern implementation
   - Database migrations

4. **DTOs** (`Models/`): Data Transfer Objects
   - `InternalEmployeeDto`: DTO for internal employees
   - `PromotionForCreationDto`: DTO for promotion creation
   - `StatisticsDto`: DTO for statistics

5. **Mapper Profiles** (`MapperProfiles/`): AutoMapper configuration
   - `EmployeeProfile`: Employee entity-to-DTO mappings
   - `StatisticsProfile`: Statistics mappings

6. **Middleware** (`Middleware/`): HTTP pipeline middleware
   - `EmployeeManagementSecurityHeadersMiddleware`: Security header injection

7. **Action Filters** (`ActionFilters/`): MVC action filters
   - `CheckShowStatisticsHeader`: Custom header validation

## Testing

The project includes extensive unit tests demonstrating various testing patterns and practices:

### Test Files
- **EmployeeServiceTests.cs**: Service layer testing
- **InternalEmployeeControllerTests.cs**: API controller testing
- **PromotionsControllerTests.cs**: Promotion endpoint testing
- **StatisticsControllerTests.cs**: Statistics endpoint testing
- **CheckShowStatisticsHeaderTests.cs**: Middleware testing
- **EmployeeFactoryTests.cs**: Factory pattern testing
- **MoqTests.cs**: Moq framework demonstrations
- **DataDrivenEmployeeServiceTests.cs**: Data-driven test examples
- **TestIsolationApproachesTests.cs**: Test isolation strategies

### Testing Patterns Demonstrated
- Unit testing with xUnit framework
- Mocking with Moq library
- Fixtures for shared test context
- Data-driven tests
- Integration testing with dependency injection
- Test isolation techniques

### Test Fixtures
- `EmployeeServiceFixture`: Basic service fixture
- `EmployeeServiceCollectionFixture`: Shared collection fixture
- `EmployeeServiceWithAspNetCoreDIFixture`: ASP.NET Core DI integration

## Technologies & Frameworks

- **Framework**: ASP.NET Core
- **ORM**: Entity Framework Core
- **Testing**: xUnit, Moq
- **Mapping**: AutoMapper
- **HTTP Clients**: HttpClient with typed clients
- **Dependency Injection**: ASP.NET Core built-in DI container
- **Language**: C# (.NET)

## Getting Started

### Prerequisites
- .NET SDK (Version 6.0 or later recommended)
- Visual Studio or Visual Studio Code
- SQL Server or LocalDB for database

### Running the Application
```bash
# Restore NuGet packages
dotnet restore

# Build the solution
dotnet build

# Apply database migrations
dotnet ef database update

# Run the API
dotnet run --project EmployeeManagement
```

### Running Tests
```bash
# Run all tests
dotnet test

# Run specific test project
dotnet test EmployeeManagement.Test
```

## API Endpoints

### Internal Employees
- `GET /api/internalemployees` - Get all internal employees
- `GET /api/internalemployees/{employeeId}` - Get specific employee
- `POST /api/internalemployees` - Create new internal employee

### Promotions
- `POST /api/promotions` - Create promotion
- `GET /api/promotions/{employeeId}` - Get employee promotions

### Statistics
- `GET /api/statistics` - Get employee statistics

## Configuration

Configuration files are provided for different environments:
- `appsettings.json`: Default configuration
- `appsettings.Development.json`: Development-specific settings

These include database connection strings and environment-specific parameters.

## Learning Resources

This project is an excellent resource for learning:
- Unit testing best practices in .NET
- Dependency injection patterns
- RESTful API design
- Entity Framework Core usage
- Test fixture patterns
- Mocking strategies
- ASP.NET Core middleware
- SOLID principles application
