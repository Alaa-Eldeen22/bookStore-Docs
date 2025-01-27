# API Documentation

## Authentication

## Register User

- **Endpoint**: `POST /api/auth/register`
- **Authentication**: Not Required (Public)
- **Description**: Registers a new user by creating an account with the provided details.

### Request Body

```json
{
  "firstname": "John",
  "lastname": "Doe",
  "mail": "john.doe@example.com",
  "password": "strongPassword123",
  "role": "user"
}
```

### Response

- **Success (201 Created)**

```json
{
  "userDetails": {
    "id": "63df43f4c1234abcd56789",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "role": "user"
  }
}
```

### Errors

- **400 Bad Request**: Missing or invalid fields in the request body.
  ```json
  {
    "error": "Invalid input. Please check your data."
  }
  ```

- **409 Conflict**: Email already registered.
  ```json
  {
    "error": "Email already used"
  }
  ```

- **500 Internal Server Error**: Unexpected server error.

---

## Login User

- **Endpoint**: `POST /api/auth/login`
- **Authentication**: Not Required (Public)
- **Description**: Logs in an existing user and returns their authentication token.

### Request Body

```json
{
  "mail": "john.doe@example.com",
  "password": "strongPassword123"
}
```

### Response

- **Success (200 OK)**

```json
{
  "userDetails": {
    "id": "63df43f4c1234abcd56789",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "role": "user"
  }
}
```

### Errors

- **401 Unauthorized**: Invalid email or password.
  ```json
  {
    "error": "There was a problem logging in. Check your email and password or create an account."
  }
  ```

- **500 Internal Server Error**: Unexpected server error.

---

