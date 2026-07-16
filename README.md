# Book Management System

A complete Spring Boot application created for the COOP Training Spring Boot Assignment.  
It manages one main business entity: `Book`.

## Technologies

- Java 17
- Spring Boot
- Spring MVC and Thymeleaf
- Spring Data JPA / Hibernate
- Spring Security with JDBC authentication
- MySQL
- Bean Validation
- Spring Boot Actuator
- OpenAPI / Swagger UI
- Maven

## Main Features

- Full CRUD REST API
- Category finder
- Sorting
- Global exception handling
- Validation and custom validation annotation
- Database-backed users and roles
- BCrypt password encoding
- MVC page that displays all books
- MVC form to add a book
- Actuator health and info endpoints
- Swagger documentation
- Postman collection

## Run in Eclipse

1. Install Java 17, MySQL, and Eclipse with Spring Tools.
2. Create the database:

```sql
CREATE DATABASE book_management_db;
```

3. Open:

```text
src/main/resources/application.properties
```

4. Replace:

```properties
spring.datasource.password=CHANGE_ME
```

with your MySQL root password. Change the username too when needed.

5. In Eclipse select:

```text
File → Import → Maven → Existing Maven Projects
```

6. Choose the project folder and click **Finish**.
7. Right-click the project:

```text
Run As → Spring Boot App
```

The application runs on:

```text
http://localhost:8081
```

## Default Accounts

The application creates these users automatically:

| Username | Password | Role |
|---|---|---|
| employee | employee123 | EMPLOYEE |
| manager | manager123 | MANAGER |
| admin | admin123 | ADMIN |

Passwords are stored as BCrypt hashes in the database.

## Role Permissions

| HTTP method | Allowed roles |
|---|---|
| GET | EMPLOYEE, MANAGER, ADMIN |
| POST | MANAGER, ADMIN |
| PUT | MANAGER, ADMIN |
| PATCH | MANAGER, ADMIN |
| DELETE | ADMIN |

## REST API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/books` | Get all books |
| GET | `/api/books?sort=price,asc` | Get all books with sorting |
| GET | `/api/books/{id}` | Get a book by ID |
| GET | `/api/books/category/{category}` | Find books by category |
| POST | `/api/books` | Create a book |
| PUT | `/api/books/{id}` | Full update |
| PATCH | `/api/books/{id}` | Partial update |
| DELETE | `/api/books/{id}` | Delete a book |

## Example JSON

```json
{
  "title": "Java Fundamentals",
  "category": "Programming",
  "price": 89.99,
  "pageCount": 420,
  "level": "BEGINNER",
  "active": true,
  "code": "JAV-103"
}
```

The code format must be three uppercase letters, a hyphen, and three digits, such as `JAV-103`.

## MVC Pages

- Book table: `http://localhost:8081/books`
- Add-book form: `http://localhost:8081/books/new`

## Swagger

```text
http://localhost:8081/swagger-ui.html
```

Use the **Authorize** button or Basic Authentication with one of the default accounts.

## Actuator

- Health: `http://localhost:8081/actuator/health`
- Info: `http://localhost:8081/actuator/info`

## Postman

Import:

```text
postman/Book_Management_API.postman_collection.json
```

The collection includes GET, POST, PUT, PATCH, DELETE, one 404 test, and one 403 test.

## Important Concepts to Explain

- **IoC:** Spring creates and manages application objects.
- **Dependency Injection:** Dependencies are supplied through constructors.
- **Bean:** An object managed by the Spring container.
- **Component scanning:** Spring searches the main package and subpackages for components.
- **@Qualifier:** Selects `EmailNotificationService` when more than one implementation exists.
- **@Primary:** Marks `SmsNotificationService` as the default implementation.
- **Prototype scope:** A new EmailNotificationService instance is created each time it is requested.
- **Repository:** Communicates with the database.
- **Service:** Contains business logic.
- **Controller:** Receives HTTP requests and delegates to the service.
- **404:** Returned when a requested book does not exist.
- **403:** Returned when an authenticated user does not have permission.
