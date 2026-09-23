# Task API — SQLite CRUD

A simple CRUD API for managing tasks, built with FastAPI and backed by a SQLite database.

## Why SQLite?

SQLite was chosen because it needs no separate server — it's just a single file (`tasks.db`) that gets created automatically. This makes it perfect for a small project like this: zero setup, and the data survives a server restart since it's stored on disk instead of in memory.

## Database file

The database lives in `tasks.db`, created automatically the first time the app runs. It is git-ignored, so every fresh clone starts with a clean database (seeded with 3 example tasks).

## How to run

```bash
pip install fastapi uvicorn
uvicorn main:app --reload
```

Then visit `http://127.0.0.1:8000/tasks` or `http://127.0.0.1:8000/docs` for interactive API docs.

## Endpoints

- `GET /tasks` — list all tasks
- `GET /tasks/{id}` — get one task
- `POST /tasks` — create a task
- `PUT /tasks/{id}` — update a task
- `DELETE /tasks/{id}` — delete a task

## Example SQL query (Stage 4)

```sql
SELECT * FROM tasks WHERE done = 1;
```

This returned only the tasks marked as completed — confirming that filtering happens directly in the database rather than in application code.