# User CRUD API

This is a simple RESTful API built with Python 3.8+ and Flask web framework for managing user entities with CRUD (Create, Read, Update, Delete) operations.

## Features

- Create new users with name and email
- Retrieve all users or a specific user by ID
- Update existing user information
- Delete users
- Uses SQLite as the database
- Input validation and error handling
- UUID for unique user identification

## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-directory>
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install flask flask-sqlalchemy
```

## Usage

1. Run the application:
```bash
python user_crud.py
```

2. The API will be available at `http://localhost:5000`

## API Endpoints

| Method | Endpoint           | Description                    | Request Body                     |
|--------|--------------------|--------------------------------|----------------------------------|
| POST   | /users            | Create a new user              | `{"name": "string", "email": "string"}` |
| GET    | /users            | Get all users                 | None                            |
| GET    | /users/<user_id>  | Get a specific user           | None                            |
| PUT    | /users/<user_id>  | Update a user                 | `{"name": "string", "email": "string"}` |
| DELETE | /users/<user_id>  | Delete a user                 | None                            |

## Example Requests

### Create User
```bash
curl -X POST http://localhost:5000/users \
-H "Content-Type: application/json" \
-d '{"name": "John Doe", "email": "john@example.com"}'
```

### Get All Users
```bash
curl http://localhost:5000/users
```

### Get Single User
```bash
curl http://localhost:5000/users/<user_id>
```

### Update User
```bash
curl -X PUT http://localhost:5000/users/<user_id> \
-H "Content-Type: application/json" \
-d '{"name": "Jane Doe", "email": "jane@example.com"}'
```

### Delete User
```bash
curl -X DELETE http://localhost:5000/users/<user_id>
```

## Response Format

Successful responses return JSON with status code 200 or 201:
```json
{
  "id": "uuid-string",
  "name": "string",
  "email": "string",
  "created_at": "iso-date-string",
  "updated_at": "iso-date-string"
}
```

Error responses return JSON with appropriate status code:
```json
{
  "error": "error message"
}
```

## Database

- Uses SQLite database stored in `users.db`
- Automatically creates the database and tables on first run
- Stores user ID (UUID), name, email, creation timestamp, and update timestamp

## Development

- The application runs in debug mode by default
- Database changes are automatically committed or rolled back on errors
- Email addresses must be unique

## License

MIT License