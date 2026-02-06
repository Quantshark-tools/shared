# quantshark-shared

Shared package for Quantshark services.

## What is inside

- SQLModel entities used by multiple services (`asset`, `contract`, funding points, etc.)
- Shared database settings (`DB_*`) and connection URL builder
- Alembic migration setup and migration history
- Reusable integration-test helpers (`quantshark_shared.testing`)

## Used by

- funding-tracker
- funding-data-api

## Local development

```bash
uv sync --dev
cp .env.example .env
```

Required variables in `.env`:

- `DB_HOST`
- `DB_PORT`
- `DB_USER`
- `DB_PASSWORD`
- `DB_DBNAME`

## Database migrations

```bash
uv run alembic upgrade head
```

Docker-based migration runner:

```bash
docker compose up --build
```

## Quality checks

```bash
uv run ruff check .
uv run pyright
```

## Test helpers

Minimal `pytest` setup:

```python
from quantshark_shared.testing.fixtures import *
```

Details: `quantshark_shared/testing/README.md`.

## License

MIT
