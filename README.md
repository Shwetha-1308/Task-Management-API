# Task-Management-API
--------------------------------
The Task Manager API is a Spring Boot–based application that allows users to create, update, view, and delete tasks.

It supports both H2 in-memory database (for quick testing) and MySQL database (for production use).

The application also includes a basic HTML page to interact with the API, plus a configured H2 database console for easy data inspection.

-------------------------------------------------------------

Features:

1)Task Management:

Create new tasks.

Retrieve all tasks or a specific task by ID.

Update task details.

Delete tasks.

2)Database Support:

H2 Database (in-memory) for development/testing.

MySQL support for persistent storage.

3)Web Interface:

Simple HTML page (index.html) to interact with the API.

Buttons to fetch all tasks, retrieve a specific task, and add new tasks.

4)API Testing:

Fully testable via Postman or any HTTP client.

Supports JSON input and output.

5)Error Handling:

Handles invalid task IDs, missing fields, and bad requests gracefully.

6)Input Validation:

Uses Spring Validation to ensure required fields are provided.

------------------------------------------------------------

Technologies Used:

1)Spring Boot – Backend framework.

2)Spring Data JPA – For database operations.

3)H2 Database – In-memory database for quick testing.

4)MySQL – Optional persistent database.

5)Lombok – To reduce boilerplate code.

6)Spring Validation – For input validation.

7)Maven – Dependency management.

8)Postman – API testing tool.

-------------------------------------------------

Setup Instructions — Task Manager API

Prerequisites

Java 22 installed and configured in your system PATH.

Maven installed for dependency management.

Postman (or any REST client) for testing the API.

An IDE such as IntelliJ IDEA, Eclipse, or VS Code with Java support.

Step 1: Create the Spring Boot Project

Using Spring Initializr Website

Go to https://start.spring.io.

Fill in the details:

Project: Maven

Language: Java

Spring Boot: 3.x.x (latest stable version)

Group: com.example

Artifact: news-aggregator-api

Java Version: 22

Add Dependencies:

Spring Web

Spring Security

Spring Data JPA

H2 Database

Validation

Lombok

Spring Boot DevTools

Click Generate to download the ZIP file.

Extract the ZIP and open the project in your IDE.

Step 2: Configure the Application

Database Configuration

By default, the app can use H2 in-memory database for testing OR MySQL for persistent storage.

For H2 Database (development/testing):

Access the H2 console at:
http://localhost:8080/h2-console

Credentials:

JDBC URL: jdbc:h2:mem:testdb

Username: sa

Password: sa

For MySQL (production use):

In application.properties update:

spring.datasource.url=jdbc:mysql://localhost:3306/taskmanagerdb

spring.datasource.username=your_mysql_username

spring.datasource.password=your_mysql_password

spring.jpa.hibernate.ddl-auto=update

Step 3: Build and Run the Application

Build the Application

mvn clean install

Run the Application

mvn spring-boot:run

Access the Application

API Base URL: http://localhost:8080

H2 Console: http://localhost:8080/h2-cons

----------------------------------------------------------------

API Documentation

Base URL

http://localhost:8080

1. Get All Tasks
   
URL: /tasks

Method: GET

Response:

[
    {
        "id": 1,
        "title": "Sample Task",
        "description": "This is a sample task",
        "deadline": "2024-05-25T12:00:00",
        "priority": "HIGH",
        "completed": false
    },
    {
        "id": 2,
        "title": "Another Task",
        "description": "This is another task",
        "deadline": "2024-05-28T15:00:00",
        "priority": "LOW",
        "completed": true
    }
]

2. Get Task by ID
   
URL: /tasks/{id}

Method: GET

Example: /tasks/2

Response:

{
    "id": 2,
    "title": "Another Task",
    "description": "This is another task",
    "deadline": "2024-05-28T15:00:00",
    "priority": "LOW",
    "completed": true
}

3. Create a New Task
   
URL: /tasks

Method: POST

Request Body:

{
    "title": "Sample Task",
    "description": "This is a sample task created using Postman",
    "deadline": "2024-05-25T12:00:00",
    "priority": "HIGH",
    "completed": false
}

Response:

{
    "id": 3,
    "title": "Sample Task",
    "description": "This is a sample task created using Postman",
    "deadline": "2024-05-25T12:00:00",
    "priority": "HIGH",
    "completed": false
}

4. Update a Task
   
URL: /tasks/{id}

Method: PUT

Request Body:

{
    "title": "Updated Task",
    "description": "This task has been updated",
    "deadline": "2024-05-30T14:00:00",
    "priority": "MEDIUM",
    "completed": true
}

Response:

{
    "id": 2,
    "title": "Updated Task",
    "description": "This task has been updated",
    "deadline": "2024-05-30T14:00:00",
    "priority": "MEDIUM",
    "completed": true
}

5. Delete a Task
   
URL: /tasks/{id}

Method: DELETE

Response:

{
    "message": "Task deleted successfully"
}

-------------------------------------------------------------
Testing the API

H2 Console:

Visit http://localhost:8080/h2-console

Username: sa

Password: sa

Postman:

Use /tasks endpoints for CRUD operations.

HTML Page (index.html):

Load in browser to interact with the API visually.

-----------------------------------------------------------------

Optional Features

Task priority sorting.

Pagination for task lists.


Search tasks by keyword.

Integration with external reminder APIs.
