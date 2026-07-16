# Book Management System

A complete Spring Boot application created for the COOP Training Spring Boot Assignment.  
It manages one main business entity: `Book`.


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
with your MySQL root password. Change the username too when needed.

4. In Eclipse select:

```text
File → Import → Maven → Existing Maven Projects
```

5. Choose the project folder and click **Finish**.
6. Right-click the project:

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



Maram Alyusef
