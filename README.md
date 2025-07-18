# CTC Health Backend Task

A NestJS + MongoDB REST API for managing users (CRUD + validation).

## Setup

1. Clone & install

   ```bash
   git clone https://github.com/KarimElhakim/ctchealth-Backend-Task.git
   cd ctchealth-Backend-Task
   npm install
   ```

2. Configure

   ```bash
   cp .env.example .env
   ```

   Edit `.env` and set:

   ```
   MONGODB_URI=your_mongo_uri   # e.g. mongodb://localhost:27017/ctchealth or Atlas URI
   PORT=3000
   ```

3. Run

   ```bash
   npm run start:dev
   ```

   The API runs at `http://localhost:3000`.

## Endpoints

* **POST** `/users`
  Create a user

  ```bash
  curl -s -X POST http://localhost:3000/users \
    -H "Content-Type: application/json" \
    -d '{"name":"Alice","email":"alice@example.com","age":30}'
  ```

* **GET** `/users`
  List all users

  ```bash
  curl -s http://localhost:3000/users
  ```

* **GET** `/users/:id`
  Get a user by ID

* **PATCH** `/users/:id`
  Update a user

  ```bash
  curl -s -X PATCH http://localhost:3000/users/<id> \
    -H "Content-Type: application/json" \
    -d '{"age":31}'
  ```

* **DELETE** `/users/:id`
  Delete a user

## Validation

Invalid payloads return **400 Bad Request**. Example:

```bash
curl -s -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{}'
```

Response:

```json
{
  "statusCode": 400,
  "message": [
    "name must be a string",
    "email must be an email",
    "age must be an integer number"
  ],
  "error": "Bad Request"
}
```

## Git

Use clear, descriptive commits:

* `feat(users): add create endpoint`
* `fix(users): handle duplicate email`
* `chore: update README`
