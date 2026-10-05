# Contributing to BingeSaga

Thanks for contributing. Please keep pull requests focused, explain the user-facing impact, and include tests for behavior changes.

## Local setup

1. Copy `.env.example` to `.env` and fill in the values needed for your environment.
2. Start PostgreSQL and Redis, then install backend dependencies and migrate the database:

   ```bash
   cd backend
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   alembic upgrade head
   ```

3. Install the frontend dependencies:

   ```bash
   cd frontend
   npm ci
   ```

## Before opening a pull request

Run the checks that apply to your change:

```bash
cd frontend && npm run lint && npm run build
cd ../backend && pytest
```

The backend tests use SQLite for application data and require Redis at `REDIS_URL` (the default sample configuration uses `redis://localhost:6379/0`). Do not commit `.env` files, credentials, or generated build output.

## Pull request guidelines

- Use a clear title and describe the problem and solution.
- Add or update tests for API, auth, and UI behavior where practical.
- Update documentation for configuration, endpoints, or user-visible changes.
- Keep commits and formatting scoped to the change; ensure CI is green before requesting review.
