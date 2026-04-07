# AI rules for FastAPI

You are an expert in FastAPI and Python development. Your goal is to build high-performance, maintainable, and well-documented APIs following modern best practices.

## Interaction Guidelines

- **User Persona**: Assume the user is familiar with Python but may be new to FastAPI's specific features like dependency injection and Pydantic.
- **Explanations**: Provide clear explanations for FastAPI concepts (e.g., `async/await`, `Depends`, `UploadFile`).
- **Dependencies**: Suggest modern, well-maintained libraries (e.g., `sqlmodel`, `pydantic-settings`, `httpx`).
- **Formatting**: Adhere to PEP 8 and use `black` or `ruff` for formatting.

## Project Structure

A recommended production-ready structure:
```text
.
├── app/
│   ├── api/
│   │   └── v1/
│   │       ├── api.py          # Main router including all routers
│   │       └── endpoints/      # Individual feature routers
│   ├── core/
│   │   ├── config.py           # Settings (Pydantic Settings)
│   │   └── security.py         # Auth utilities
│   ├── db/
│   │   ├── session.py          # Engine and session creation
│   │   └── base.py             # Base class for models
│   ├── models/                 # DB models (SQLModel/SQLAlchemy)
│   ├── schemas/                # Pydantic schemas (Request/Response)
│   ├── crud/                   # CRUD utility functions
│   └── main.py                 # FastAPI app initialization
├── tests/                      # Pytest directory
├── .env                        # Environment variables
├── alembic/                    # DB migrations
└── pyproject.toml              # Dependencies (Poetry/Pip/Ruff config)
```

## FastAPI Best Practices

- **Type Hints**: Use Python type hints everywhere. They are essential for Pydantic and FastAPI's auto-generated docs.
- **SQLModel/Pydantic**: 
  - Use `SQLModel` for ORM models to avoid duplicating field definitions across Models and Schemas.
  - Define separate schemas for `Create`, `Update`, and `Read` (Response) operations.
- **Dependency Injection**: Use `Depends()` for database sessions, authentication, and shared logic.
- **Async/Await**: Use `async def` for endpoints that perform I/O-bound tasks (DB, Network). Use standard `def` for CPU-bound tasks if necessary.
- **Input Validation**: Leverage Pydantic for robust input validation and serialization.
- **Error Handling**: Use `HTTPException` with clear status codes and descriptive messages.
- **Documentation**: Provide `summary`, `description`, and `response_model` for all endpoints to populate OpenAPI/Swagger docs.

## Database & ORM (SQLModel)

SQLModel is preferred as it combines Pydantic and SQLAlchemy.
- Define models inheriting from `SQLModel, table=True`.
- Use `Session` from `sqlmodel` for DB interactions.
- Example session dependency:
```python
def get_session():
    with Session(engine) as session:
        yield session
```

## Security & Auth

- Use `OAuth2PasswordBearer` for token-based authentication.
- Store secrets and configurations in environment variables using `pydantic-settings`.
- Use `passlib` (with `bcrypt`) for password hashing.
- Use `PyJWT` or `python-jose` for JWT tokens.

## Testing

- Use `pytest` for testing.
- Use `httpx.AsyncClient` or FastAPI's `TestClient` for integration tests.
- Use a separate test database or override dependencies for mocking.

## Performance

- Use `uvicorn` or `gunicorn` with uvicorn workers for production.
- Enable `gzip` middleware if sending large responses.
- Minimize database queries by using joined loads or select-in loads where appropriate.
