# dual-job-dating

## Table of Contents

- [Description & Contributors](#description--contributors)
- [Installation](#installation)
  - [Flutter App](#flutter-app)
  - [Angular App](#angular-app)
  - [ASP.NET Core App](#aspnet-core-app)
- [Usage](#usage)
  - [Angular App Instructions](#angular-app-instructions)
    - [Admin](#admin)
    - [Company](#company)
  - [Flutter App](#flutter-app)
    - [Student](#student)
- [Screenshots](#screenshots)
- [Technical Details](#technical-details)
- [Database Schema](#database-schema)
- [API Documentation](#api-documentation)
- [CI/CD](#cicd)
- [License](#license)
- [Contact](#contact)

## Description & Contributors

This is an open source project for creating a platform for dual job dating. The project is developed by students of Mobile Software Development (MSD21) at the University of Applied Studies in Kapfenberg, Austria. The project was supervised by FH-Prof. DI Dr. Elmar Krainz, DI (FH) Michael Ulm, MA, and DI (FH) Andreas Öffl, MSc.

## Installation

The project is divided into three parts.. The frontend consists of a Flutter application and an Angular application, while the backend is a ASP.NET Core application. The following instructions will guide you through the installation process.

### Installation steps

#### Flutter App

1. Clone the [repository](https://github.com/FH-JOANNEUM-MSD/dual-job-date-mobile)

2. Navigate to the `dual-job-date-mobile` directory

3. Install Flutter [Flutter](https://docs.flutter.dev/get-started/install)

4. Run the application with an emulator or your physical device as an emulator

#### Angular App

1. Clone the [repository](https://github.com/FH-JOANNEUM-MSD/dual-job-date-web.git)

2. Make sure you have Node.js and Angular installed

3. Navigate to `dual-job-date-web` directory and install the required npm modules:
   ```
    npm install
   ```
4. Run the application in developer mode:
   ```
    ng serve
   ```
5. Navigate to http://localhost:4200/. The application will automatically reload if you change any of the source files.

#### ASP.NET Core App

1. Clone the [repository](https://github.com/FH-JOANNEUM-MSD/dual-job-date-api.git)
2. Make sure you have [Docker](https://docker.com) installed
3. Navigate to the `DualJobDateAPI` directory
4. Create the docker container (database and API)
   ```
   docker-compose -f docker-compose-dev.yml up -d
   ```
   The application will be started within a docker container in developer mode on [localhost:8000](http://localhost:8000) using another docker container as database on [localhost:3306](http://localhost:3306)
5. Alternatively, run the application in developer mode in an IDE with [.NET8](https://learn.microsoft.com/en-gb/dotnet/core/install/) and [EF-Core tools](https://learn.microsoft.com/en-gb/ef/core/cli/dotnet) installed (Docker still needed for the database and database must be migrated manually).
6. Open [Swagger](http://localhost:8000/swagger/index.html)

For more details read Readme.md in the respective repositories.

For style guidelines, prototyping, and design details, please refer to the following document:

[UI/UX Design on Figma](https://www.figma.com/design/HvKCRzlJDUp7VPEmllLSXy/UI%2FUX?node-id=1-3)

## Usage

Starting from the third semester, dual studies at FH JOANNEUM allow students to alternate between academic instruction and part-time employment at various companies, providing practical, industry-specific experience. The "Dual Job Dating" app is designed to facilitate job matchmaking between students and patner companies. It allows students to browse company profiles, express their preferences through likes or dislikes, and receive appointment schedules based on their choices for the job dating event. Additionally, the app includes a web-based component for administrative management of the entire process by both the educational institution and the participating companies.

### Instructions for use

### Angular App Instructions

The Angular web app is for administrators and companies only: [Dual Job Dating Web](https://dual-job-dating.msd-moss-prod.fh-joanneum.at/)

#### Admin

**Account Setup**

- Admin accounts are created by FH Joanneum.

**Usage**

- **Login:** Enter your credentials.
- **Start Page:** Generate appointments by selecting dates and programs.
- **Company Page:** View, search, filter, and edit company details. Add companies via form or Excel import.
- **Student Page:** Manage student accounts similarly.
- **Profile:** Edit company profiles and view appointments.
- **Account Management:** Change your password or log out.

#### Company

**Account Setup**

- Company accounts are created by FH Joanneum.
- Receive your password via email.
- Create a new password on the first login.

**Usage**

- **Login:** Enter your credentials.
- **Edit Details:** Update company info and set status to inactive if not participating.
- **Appointments:** View your appointment list.
- **Account Management:** Change your password or log out.

For assistance, contact the app admin.

### Flutter App

#### Student

As a student the app can be downloaded in the Google Play Store and the Apple App Store.

[Google Play Store](https://play.google.com/store/apps/details?id=at.fhj.dual_job_date_mobile&hl=de_AT)

[Apple App Store](https://apps.apple.com/at/app/dualdating/id6499212782?l=en-GB)

#### Steps for your account

- To receive a password the admin of the FH Joanneum has to create an user
- The user receives a password per email
- On the first login the user has to create a new password

#### Usage of the app

- To login to the app the user has to fill out the needed credentials in the login screen
- At the first login, the user has to create a new, safe password
- On the main screen the user can like or dislike companies that are listed for the job dating
- On the appointment screen, the user can choose an appointment for the liked companies
- On the more screen, the user can lookup the imprint and the data protection of the FH Joanneum and change the first and last name if needed

For assistance, contact the app admin.

### Screenshots

Web app screenshots are shown below:

<img src="/Assets/AppScreenshots/startseite_web.png" width="500" height="250">

<img src="/Assets/AppScreenshots/companies_web.png" width="500" height="200">

<img src="/Assets/AppScreenshots/company_profile.png" width="500" height="500">

<img src="/Assets/AppScreenshots/newCompany.png" width="250" height="250">

The following screenshots are from the Flutter app and how it looks like on a mobile phone

<img src="/Assets/AppScreenshots/Login.png" width="250" height="500">

<img src="/Assets/AppScreenshots/ResetPassword.png" width="250" height="500">

<img src="/Assets/AppScreenshots/FirstLogin.png" width="250" height="500">

<img src="/Assets/AppScreenshots/Companies.png" width="250" height="500">

<img src="/Assets/AppScreenshots/Appointments.PNG" width="250" height="500">

<img src="/Assets/AppScreenshots/MoreScreen.png" width="250" height="500">

<img src="/Assets/AppScreenshots/MoreScreen2.png" width="250" height="500">

## Technical Details

### Tech stack

#### BLoC

[Link to the library](https://bloclibrary.dev/)

We used the BLoC library (Business Logic Component) in our project to seperate the presentation from business logic, be able to code fast and most importantly, make the code reusable.

BLoC was created so the developer

- knows what the state of the application is at any point
- can easily test every case to make sure the app is responding appropriatly
- record every single user interaction in the application so data-driven decisions can be made
- can work as efficiently as possible and reuse components both within the application and across other applications
- can have many developers working seamlessly within a single code base following the same patterns and conventions
- develop fast and reactive apps

In all places, where a connection to the Rest API is required, BLoC is used.

For more details read [here](https://github.com/FH-JOANNEUM-MSD/dual-job-date-mobile/blob/development/README.md).

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

### CI/CD

This project utilizes Continuous Integration and Continuous Deployment (CI/CD) to streamline development and deployment processes. CI/CD ensures that code changes are automatically tested, integrated, and deployed, providing rapid feedback and reducing the risk of integration issues. To implement the cicd process, a separate github actions pipeline was created for web-,mobile-,backend-development.
Feedback on if a workflow run was successful gets automatically sent to a discord group.

#### Backend/API

The CI/CD pipeline for the Dual Job Dating project, defined in a YAML file for GitHub Actions, triggers on push or pull request events to the cicd/notification branch. It includes four main jobs: build, test, build-and-push-docker, and notification jobs for failure and success. The build job checks out the code, sets up .NET Core, restores dependencies, builds the project, and caches NuGet packages. The test job runs the project tests after the build job. The build-and-push-docker job logs into GitHub Container Registry, builds, and pushes the Docker image. The pipeline requires manual deployment to a Kubernetes cluster and has permissions to read contents and write packages.

#### Web

The Dual Job Dating Web CI/CD Pipeline for the Angular project automates building, testing, and deployment to the GitHub Container Registry, triggered by push or pull request events to the main branch, and release creation. The pipeline includes three main jobs: test, build, and deploy. The test job checks out the code, sets up Node.js, installs dependencies, and runs tests. The build job checks out the code, sets up Node.js, installs dependencies, generates the API, builds the application, and saves the build artifact. The deploy job checks out the code, converts the repository name to lowercase, downloads the build artifact, logs into the GitHub Container Registry, and builds and pushes the Docker image. Manual deployment to a Kubernetes cluster is required.

#### Mobile

The Dual Job Dating Mobile CI/CD Pipeline for the Flutter project automates building, testing, signing and in the future deployment to the playstore and appstore. The build and test steps are triggered on push or pull request events to the main branch, the deployment step is triggered by realease creation on the main branch. The test job checks out the code, sets up flutter, caches the flutter dependencies, installs dependencies and runs tests. The build job separated for iOS and Android automatically builds and signs the app bundles, currently they get stored as a workflow artifact, with automatic deployment to internal playstore tracks and testflight (defined in the deployment steps) in the works.

## License

[MIT License](LICENSE)

## Contact

For any questions or feedback, please contact us at:

https://www.fh-joanneum.at/msd

Email: msd@fh-joanneum.at

Tel: +43 316 5453 - 6332
