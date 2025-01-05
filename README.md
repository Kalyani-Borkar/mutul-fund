# Mutual Fund App API

This Spring Boot application allows users to **register**, **log in**, and **fetch mutual fund data**.

## Prerequisites

- **JDK 11** or higher
- **Maven** for building the project

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/Kalyani-Borkar/mutul-fund.git
    ```

2. Navigate into the project folder:

    ```bash
    cd mutual-fund-app
    ```

3. Build and run the project:

    ```bash
    mvn spring-boot:run
    ```

The app will be available at `http://localhost:8080`.

## API Endpoints

### 1. **Register User**
- **URL**: `api/users/register`
- **Method**: `POST`
- **Body** (JSON):
    ```json
    {
        "username": "john_doe",
        "password": "password123"
    }
    ```
- **Response**: 
    - Success: `{"message": "User registered successfully"}`
    - Error: `{"error": "Registration failed"}`
  
---

### 2. **Login User**
- **URL**: `api/users/login`
- **Method**: `POST`
- **Body** (JSON):
    ```json
    {
        "username": "john_doe",
        "password": "password123"
    }
    ```
- **Response**: 
    - Success: `{"message": "Login successful", "token": "<JWT-TOKEN>"}`
    - Error: `{"error": "Invalid credentials"}`
  
---

### 3. **Fetch Mutual Funds**
- **URL**: `/api/mutualfunds/fetch`
- **Method**: `GET`
- **Query Parameters**:
    - `schemeType`: (Optional, default: `Open`)

    Example:
    ```bash
    GET http://localhost:8080/api/mutualfunds/fetch?schemeType=Open
    ```

- **Response**:
    - Success: 
        ```json
        {
            "funds": [
                { "name": "Fund Name 1", "nav": 100.0, "schemeType": "Open" },
                { "name": "Fund Name 2", "nav": 150.5, "schemeType": "Open" }
            ]
        }
        ```
    - Error: 
        ```json
        { "error": "Failed to fetch mutual funds data: <error_message>" }
        ```

---

## Example cURL Commands

- **Register**:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"username": "john_doe", "password": "password123"}' http://localhost:8080/api/register
    ```

- **Login**:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"username": "john_doe", "password": "password123"}' http://localhost:8080/api/login
    ```

- **Fetch Mutual Funds**:
    ```bash
    curl "http://localhost:8080/api/mutualfunds/fetch?schemeType=Open"
    ```

---

## Error Handling

The API returns error messages in JSON format, e.g.,

```json
{
    "error": "Invalid credentials"
}
```
  
