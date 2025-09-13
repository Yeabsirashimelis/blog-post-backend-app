# 🏋️ Workout Tracking API

A RESTful API for tracking workouts and their entries. Built entirely in Go with PostgreSQL, supporting full CRUD operations.

## ✨ Features
- User registration & authentication (JWT)
- Create, read, update, and delete workouts and workout entries
- PostgreSQL database
- Clean, modular Go codebase
- Simple setup — no external environment configuration required

## 🛠 Tech Stack
- Go 1.22+
- PostgreSQL
- net/http (and router if used)
- Docker support for running PostgreSQL

## 🚀 Getting Started

1. **Clone the repository**
   ```
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. **Start PostgreSQL**
   You can use Docker or a local Postgres instance:
   ```
   docker compose up -d
   ```

3. **Configure database in code**  
   The database connection is set directly in Go code (look in `database.go` package). Example:
   ```go
   db, err := sql.Open("postgres", "postgres://postgres:postgres@localhost:5432/workouts?sslmode=disable")
   ```

4. **Run Migrations**  
   Apply SQL migrations included in the `migrations/` folder using `goose` or `psql`:
   ```
   goose up
   ```

5. **Run the API**
   ```
   go run main.go
   ```
   The API will be available at `http://localhost:8080`.

## 🗂 Project Structure
```
.
├── cmd/
│   └── server/       # main entry point
├── internal/
│   ├── store/        # DB queries & models
│   ├── handlers/     # HTTP handlers
│   ├── middleware/   # auth, logging
│   └── auth/         # JWT helpers
├── migrations/       # SQL migration files
└── README.md
```

## 🧪 Example Requests
-for the api calls use curl or user whatever api testing tools like "POSTMAN"
Create a workout:
```
curl -X POST http://localhost:8080/api/workouts \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"title":"Leg Day","description":"Squats & lunges","duration_minutes":60}'
```

## 🛠 Development Tips
- Run `go fmt ./...` before commits to keep formatting clean.
- Use `go test ./...` to run unit tests.
- Hardcoded configuration makes it simple to run, but remember to change database credentials for production.

MIT © 2025 [Your Name]

