# Kanban Board API

Esta es la documentación de la API para la aplicación web de tablero Kanban. La API permite a los usuarios crear, modificar y gestionar "cards" y "columns", e incorpora un sistema completo de autenticación y autorización.

## Endpoints

### Autenticación y Autorización

#### POST /api/register
### Request
This API endpoint makes an HTTP POST request to localhost:3000/api/register to register a new user. The request body should include the following parameters:

- `username`: (text) The username of the user to be registered.
    
- `email`: (text) The email address of the user to be registered.
    
- `password`: (text) The password of the user to be registered.
    

### Response

The response will include the registration status and any additional details related to the registration process.


#### POST /api/login
### API Request Description

This API endpoint is a POST request to localhost:3000/api/login. It is used for user authentication by providing the email and password in the request body.

#### Request Body

- **email** (text) - The email address of the user.
    
- **password** (text) - The password of the user.
    

#### Response

Upon successful execution, the API returns a 200 status with a JSON response containing a message.


# Section API Endpoints

## Endpoints

### Create a Section

- **URL:** `/sections/:id_user`
- **Method:** `POST`
- **Middleware:** `authMiddleware`
- **Description:** Creates a new section for a user.
- **Request Parameters:**
  - `id_user` (path): The ID of the user for whom the section is being created.
- **Request Body:** JSON object containing the details of the section.
- **Responses:**
  - `201 Created`: Section successfully created.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.

### Get Sections

- **URL:** `/sections/:id_user`
- **Method:** `GET`
- **Middleware:** `authMiddleware`
- **Description:** Retrieves all sections for a user.
- **Request Parameters:**
  - `id_user` (path): The ID of the user whose sections are being retrieved.
- **Responses:**
  - `200 OK`: Successfully retrieved sections.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.

### Update a Section

- **URL:** `/sections/:id_section`
- **Method:** `PUT`
- **Middleware:** `authMiddleware`
- **Description:** Updates a specific section.
- **Request Parameters:**
  - `id_section` (path): The ID of the section to be updated.
- **Request Body:** JSON object containing the updated details of the section.
- **Responses:**
  - `200 OK`: Section successfully updated.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `404 Not Found`: Section not found.
  - `500 Internal Server Error`: Server error.

### Delete a Section

- **URL:** `/sections/:id_section`
- **Method:** `DELETE`
- **Middleware:** `authMiddleware`
- **Description:** Deletes a specific section.
- **Request Parameters:**
  - `id_section` (path): The ID of the section to be deleted.
- **Responses:**
  - `200 OK`: Section successfully deleted.
  - `401 Unauthorized`: User is not authenticated.
  - `404 Not Found`: Section not found.
  - `500 Internal Server Error`: Server error.

### Get All Sections of User

- **URL:** `/sections`
- **Method:** `GET`
- **Middleware:** `authMiddleware`
- **Description:** Retrieves all sections of the authenticated user.
- **Responses:**
  - `200 OK`: Successfully retrieved all sections of the user.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.


# Task API Endpoints

## Endpoints

### Create a Task

- **URL:** `/tasks/:id_section`
- **Method:** `POST`
- **Middleware:** `authMiddleware`
- **Description:** Creates a new task within a section.
- **Request Parameters:**
  - `id_section` (path): The ID of the section where the task is being created.
- **Request Body:** JSON object containing the details of the task.
- **Responses:**
  - `201 Created`: Task successfully created.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.

### Get Tasks

- **URL:** `/tasks/:id_section`
- **Method:** `GET`
- **Middleware:** `authMiddleware`
- **Description:** Retrieves all tasks within a section.
- **Request Parameters:**
  - `id_section` (path): The ID of the section whose tasks are being retrieved.
- **Responses:**
  - `200 OK`: Successfully retrieved tasks.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.

### Update a Task

- **URL:** `/tasks/:id_task`
- **Method:** `PUT`
- **Middleware:** `authMiddleware`
- **Description:** Updates a specific task.
- **Request Parameters:**
  - `id_task` (path): The ID of the task to be updated.
- **Request Body:** JSON object containing the updated details of the task.
- **Responses:**
  - `200 OK`: Task successfully updated.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `404 Not Found`: Task not found.
  - `500 Internal Server Error`: Server error.

### Delete a Task

- **URL:** `/tasks/:id_task`
- **Method:** `DELETE`
- **Middleware:** `authMiddleware`
- **Description:** Deletes a specific task.
- **Request Parameters:**
  - `id_task` (path): The ID of the task to be deleted.
- **Responses:**
  - `200 OK`: Task successfully deleted.
  - `401 Unauthorized`: User is not authenticated.
  - `404 Not Found`: Task not found.
  - `500 Internal Server Error`: Server error.

### Update Task Section

- **URL:** `/tasks/:id_task`
- **Method:** `PATCH`
- **Middleware:** `authMiddleware`
- **Description:** Updates the section of a specific task.
- **Request Parameters:**
  - `id_task` (path): The ID of the task whose section is being updated.
- **Request Body:** JSON object containing the updated section details.
- **Responses:**
  - `200 OK`: Task section successfully updated.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `404 Not Found`: Task not found.
  - `500 Internal Server Error`: Server error.

### Get All Tasks of User

- **URL:** `/tasks`
- **Method:** `GET`
- **Middleware:** `authMiddleware`
- **Description:** Retrieves all tasks of the authenticated user.
- **Responses:**
  - `200 OK`: Successfully retrieved all tasks of the user.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.


# User API Endpoints

## Endpoints

### Get User Profile

- **URL:** `/user/profile`
- **Method:** `GET`
- **Description:** Retrieves the profile information of the authenticated user.
- **Middleware:** `authMiddleware` (Assumed to be required for authentication)
- **Responses:**
  - `200 OK`: Successfully retrieved user profile.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.

### Update User Profile

- **URL:** `/user/profile`
- **Method:** `PUT`
- **Description:** Updates the profile information of the authenticated user.
- **Middleware:** `authMiddleware` (Assumed to be required for authentication)
- **Request Body:** JSON object containing the updated details of the user profile.
- **Responses:**
  - `200 OK`: User profile successfully updated.
  - `400 Bad Request`: Validation error or missing parameters.
  - `401 Unauthorized`: User is not authenticated.
  - `500 Internal Server Error`: Server error.


# Database Configuration

## Environment Variables

To connect to the database and configure JWT, we need to set the following environment variables:

### Database

- **`DB_USER`**: The database user name.
- **`DB_HOST`**: The database host address.
- **`DB_DATABASE`**: The name of the database.
- **`DB_PASSWORD`**: The database user password.
- **`DB_PORT`**: The port on which the database is listening.

### JWT

- **`JWT_SECRET`**: The secret key used to sign JWT tokens.

## Example `.env` File

Create a `.env` file in the root of your project and add the following lines with your database and JWT configuration values:

