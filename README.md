# Simple Task Server

A minimal Express backend with AWS RDS (PostgreSQL) for task management.

## Features

- **POST /tasks** - Create a new task
- **GET /tasks** - List all tasks
- **GET /health** - Health check endpoint

## Database Schema

```sql
tasks (
  id SERIAL PRIMARY KEY,
  title TEXT NOT NULL
)
```

## Setup & Run

1. Create a `.env` file with your AWS RDS connection details:
```bash
DB_HOST=your-rds-endpoint.region.rds.amazonaws.com
DB_USER=your-username
DB_PASSWORD=your-password
DB_NAME=your-database-name
DB_PORT=5432
PORT=3000
```

2. Install dependencies and start:
```bash
npm install
npm start
```

Server runs on `http://localhost:3000`

## API Examples

### Create a task
```bash
curl -X POST http://localhost:3000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Buy groceries"}'
```

Response:
```json
{"id":1,"title":"Buy groceries"}
```

### List all tasks
```bash
curl http://localhost:3000/tasks
```

Response:
```json
[
  {"id":1,"title":"Buy groceries"},
  {"id":2,"title":"Write code"},
  {"id":3,"title":"Read book"}
]
```
