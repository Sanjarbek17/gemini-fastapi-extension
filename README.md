# Gemini FastAPI Extension

A comprehensive extension for Google Gemini (Antigravity) that provides expert-level FastAPI development rules, commands, and project structures.

This extension is designed to help you build high-performance, maintainable, and modern APIs with FastAPI, Python, and SQLModel.

## 🚀 Features

- **Standardized Project Structure**: Automatically initialize production-ready FastAPI project layouts.
- **AI Expert Rules**: Pre-configured guidelines for dependency injection, type hinting, pydantic 2.0, and async/await best practices.
- **Smart Commands**:
  - `init-structure`: Bootstrap a new FastAPI project structure.
  - `create-model`: Generate SQLModel database models quickly.
  - `create-schema`: Generate Pydantic request/response schemas.
  - `add-endpoint`: Quickly add new API endpoints with routers.
  - `add-to-main`: Helper to register routers in the main application.

## 📦 Installation

To use this extension, copy this directory into your Gemini extensions folder or point your Gemini configuration to this directory.

```bash
# Clone the repository
git clone git@github.com:Sanjarbek17/gemini-fastapi-extension.git
```

## 🛠 Usage

Once the extension is active, you can use the commands directly in your Gemini chat.

Example command:
> "Use the fastapi extension to initialize a new project structure."

## 📂 Project Structure

This extension suggests and automates the following structure:
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

## 📜 FastAPI Best Practices Included

- **Type Hints**: Mandatory for Pydantic validation and auto-docs.
- **SQLModel**: Combined ORM and Pydantic models to reduce duplication.
- **Dependency Injection**: Heavy use of `Depends()` for cleaner logic.
- **Modern Libraries**: Recommends `sqlmodel`, `pydantic-settings`, and `httpx`.

---

Developed by [Sanjarbek17](https://github.com/Sanjarbek17).
