# dual-job-dating

## Description & Contributors

This is an open source project for creating a platform for dual job dating. The project is developed by students of Mobile Software Development (MSD21) at the University of Applied Studies in Kapfenberg, Austria. The project was supervised by FH-Prof. DI Dr. Elmar Krainz, DI (FH) Michael Ulm, MA, and DI (FH) Andreas Öffl, MSc.

## Installation

The project is divided into three parts.. The frontend consists of a Flutter application and an Angular application, while the backend is a ASP.NET Core application. The following instructions will guide you through the installation process.

### Installation steps

#### Flutter App

1. Clone the repository

2. Navigate to the `this-directory` directory

3. Install the required dependencies

...

4. Run the application

#### Angular App

1. Clone the repository

...

#### ASP.NET Core App

1. Clone the [repository](https://github.com/FH-JOANNEUM-MSD/dual-job-date-api.git)
2. Make sure you have [Docker](https://docker.com) installed
3. Navigate to the `DualJobDateAPI` directory
4. Create the docker container (database and API)
    ```
    docker-compose -f docker-compose-dev.yml up -d
    ````
   The application will be started within a docker container in developer mode on [localhost:8000](http://localhost:8000) using another docker container as database on [localhost:3306](http://localhost:3306)
5. Alternatively, run the application in developer mode in an IDE with [.NET8](https://learn.microsoft.com/en-gb/dotnet/core/install/) and [EF-Core tools](https://learn.microsoft.com/en-gb/ef/core/cli/dotnet) installed (Docker still needed for the database and database must be migrated manually).
6. Open [Swagger](http://localhost:8000/swagger/index.html)

## Usage

Starting from the third semester, dual studies at FH JOANNEUM allow students to alternate between academic instruction and part-time employment at various companies, providing practical, industry-specific experience. The "Dual Job Dating" app is designed to facilitate job matchmaking between students and patner companies. It allows students to browse company profiles, express their preferences through likes or dislikes, and receive appointment schedules based on their choices for the job dating event. Additionally, the app includes a web-based component for administrative management of the entire process by both the educational institution and the participating companies.

### Instructions for use

### Screenshots

## Technical Details

### Tech stack

#### ASP.NET Core App

The ASP.NET Core App leverages a modern and robust technology stack designed to support scalable and secure web applications:

- **Framework**: [.NET 8.0](https://dotnet.microsoft.com/en-us/)
    - The latest iteration of Microsoft's .NET framework, providing advanced features for building high-performance applications.

- **Web API**: [ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/)
    - A framework for building web APIs on .NET, known for its high performance and scalability.

- **Authentication**: [Json Web Token (JWT)](https://jwt.io/)
    - A compact and self-contained way for securely transmitting information between parties as a JSON object, extensively used in token-based authentication.

- **API Documentation**: [Swagger](https://swagger.io/)
    - An Interface Description Language for describing RESTful APIs expressed using JSON. Swagger is used to produce interactive API documentation that can be used to test API endpoints.

- **ORM**: [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/)
    - Microsoft's modern, open-source, and cross-platform Object-Relational Mapping (ORM) framework, enabling .NET developers to work with a database using .NET objects.

- **Database**: [MySQL](https://dev.mysql.com/)
    - MySQL is a popular open-source relational database management system that integrates smoothly with Entity Framework Core for data access operations.

- **Object Mapping**: [AutoMapper](https://automapper.org/)
    - A library that simplifies the code for mapping one object to another, enhancing code readability and maintainability.

- **Identity Management**: [AspNetCore.Identity](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/identity)
    - Extends Entity Framework Core to support ASP.NET Core Identity, an API that supports user interface (UI) login functionality. This integration facilitates the management of users, passwords, profile data, roles, claims, tokens, and more.

- **Testing Frameworks**:
    - [Dotnet Test](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-dotnet-test): The primary testing SDK for .NET, which enables running tests and collecting test results in .NET projects. Essential for integrating with continuous integration systems.

    - [xUnit](https://xunit.net): An open-source, community-focused unit testing tool for the .NET framework. Known for its extensibility and support for modern testing practices, making it ideal for writing clean and maintainable test codes.

    - [Moq](https://github.com/devlooped/moq): A popular and versatile mocking framework for .NET. Moq is crucial for creating effective mock objects in unit tests, allowing developers to simulate and verify interactions between components without relying on actual implementations.

### Architecture

#### App Development with Flutter

![Flutter Architecture](Assets/flutter.png)

- UI Layer: Uses singular components for screens, focusing on user experience​

- BLoC Layer: Interface between UI and Services. Manages state and separates business logic for readability​

- Services Layer: Contains logic for external interactions like API calls. Aimed at decoupling the application core from external dependencies​

- Additional Classes: Enhances code with static helpers for UI consistency and validation

#### Web Development with Angular

![Angular Architecture](Assets/web.png)

- Model: Encapsulates the application's business objects, holding data. It's the reusable code part that simply manages the data of the application​

- View: What the user ultimately sees. It's the platform-specific UI that displays formatted data. The View is designed to present data contained in the Model​

- ViewModel: Acts as the link between the Model and View, handling logic and data preparation for the View. It retrieves data from the Model and formats it for presentation​

#### Backend Development with ASP.NET Core

![ASP.NET Core Architecture](Assets/backend.png)

- API Layer: Interfaces with the client side, handling HTTP requests via Controllers. ​

- Business Logic Layer: Processes business operations, implemented by Services, and aided by Helper functions for shared utility tasks.​

- Data Access Layer: Manages the data lifecycle with Repositories handling data transactions and the Unit of Work ensuring data integrity.​

- Business Objects: Comprise DTOs (Data Transfer Objects) and Entities, forming the data structure used across Business Logic and Data Access layers.​

- Database Initialization: Involves DbInitializer for database setup and DbSeeder for seeding initial data.​

- .NET Core Identity: Secures the application with comprehensive user and role management using UserManager, SignInManager, and RoleManager.​

### Database schema

![Database Schema](Assets/db.png)

- User and Role Entities: Core Identity framework entities where User inherits from IdentityUser and Role from IdentityRole, central to the system's security and access management.​

- UserType Enumerations: Specific roles including Admin, Institution, Company, and Student, dictating access privileges and functional scope within the system.​

- Institution and Academic Program Relationships: Hierarchical relation where Institutions may contain multiple Academic Programs, integral for structuring the educational offerings within the system.​

- Company and Academic Engagement: Defines the linkage between companies and academic programs, vital for capturing interactions such as internships.​

- Seeding and Initial Data: DbSeeder's role in populating the database with initial, essential data sets, such as predefined user roles and academic program details.​

### API documentation

#### Version 1.0

**The DualJobDate API** provides comprehensive endpoints for managing data related to companies, users, institutions, and academic programs. It is especially useful for educational institutions and companies participating in dual study programs.

#### Endpoint Groups

1. **Company Endpoints**
   - **Purpose**: Manage company profiles, update details, retrieve active companies, and manage company-specific information.
   - **Examples**:
      - Retrieve company details
      - Update company information
      - Manage active status of companies
      - Register new companies

2. **User Endpoints**
   - **Purpose**: Handle user registration, authentication, password management, and retrieve specific user data.
   - **Examples**:
      - User registration and authentication
      - Refresh authentication tokens
      - Manage passwords (change and reset)

3. **StudentCompany Endpoints**
   - **Purpose**: Manage interactions between students and companies, like adding or removing likes/dislikes.
   - **Examples**:
      - Add or remove likes/dislikes
      - Retrieve likes/dislikes based on student or company

4. **Util Endpoints**
   - **Purpose**: Provide utilities for managing and retrieving data about institutions and academic programs.
   - **Examples**:
      - Retrieve institutions and academic programs
      - Add or update academic programs

#### Authorization and Security

- **OAuth2 with JWT**: Secure access through OAuth2 using JWT tokens. Authentication requires `Authorization: Bearer {token}` header.
- **Roles and Scopes**: Different authorization levels are required such as admin, student, or institution-specific roles.

#### Important Information

- **Content Types**: Supports `application/json`, `text/json`, and `application/*+json`.
- **Responses**: Uses standard HTTP response codes like `200` (Success), `401` (Unauthorized), and `403` (Forbidden).
- **Versioning**: API versions are marked and should be considered to maintain compatibility.

#### Swagger

For detailed API usage and interactive testing, please refer to the [Swagger documentation](https://dual-dating-backend.msd-moss-test.fh-joanneum.at/swagger/index.html).


## License

[MIT License](LICENSE)

## Contact

For any questions or feedback, please contact us at:

https://www.fh-joanneum.at/msd
Email: msd@fh-joanneum.at
Tel: +43 316 5453 - 6332
