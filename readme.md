# Freelancer Project Management System

## Overview

The **Freelancer Project Management System** is a web application designed to help freelancers efficiently manage their projects. The system allows users to create, update, view, and delete projects, manage their payment status, and handle authentication through token-based authentication (JWT).

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB
- **Authentication**: JWT (JSON Web Token)
- **Other Libraries**:
  - **bcrypt** for hashing passwords
  - **cookie-parser** for handling cookies
  - **csv-parser** for CSV file parsing
  - **json2csv** for CSV file export

## API Endpoints

### User Endpoints

1. **POST /user/signup**

   - Registers a new user with username, email, password, and role.
   - **Request body**:
     - `username`: String (required)
     - `email`: String (required)
     - `password`: String (required)

2. **POST /user/login**

   - Logs in an existing user using email and password.
   - **Request body**:
     - `email`: String (required)
     - `password`: String (required)

3. **POST /user/logout**
   - Logs out the user by clearing the authentication token.

### Project Endpoints

1. **GET /project/all**

   - Fetches all projects from the database.
   - **Response**: List of all projects.

2. **GET /project/:id**

   - Fetches a project by its unique ID.
   - **Response**: Project details.

3. **POST /project/create**

   - Creates a new project.
   - **Request body**:
     - `title`: String (required)
     - `details`: String (required)
     - `dueDate`: Date (required)

4. **PATCH /project/update/:id**

   - Updates an existing project by its ID.
   - **Request body**: Updated project details (any of the project fields).
   - **Authorization**: Required (only the user who created the project can update it).

5. **DELETE /project/delete/:id**

   - Deletes a project by its ID.
   - **Authorization**: Required (only the user who created the project can delete it).

6. **POST /project/submit/:id**

   - Marks a project as completed.
   - **Authorization**: Required (only the project owner can submit the project).

7. **POST /project/payment/:id**

   - Marks the payment status of the project as completed.
   - **Authorization**: Required (only the project owner can mark the payment).

8. **POST /project/import**

   - Imports multiple projects from a CSV file.
   - **Request body**: CSV file (multipart/form-data)
   - **Authorization**: Required

9. **GET /project/export**
   - Exports all projects into a CSV file.

### Authentication Middleware

- **Authorization**: JWT tokens are used to authenticate and authorize users. Every protected endpoint requires the user to be logged in and provides the token via cookies.

---
