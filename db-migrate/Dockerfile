FROM ghcr.io/astral-sh/uv:python3.13-bookworm-slim

# Set working directory
WORKDIR /app
# Install git for dependencies from GitHub
RUN apt-get update && apt-get install -y git python3-dev libpq-dev && rm -rf /var/lib/apt/lists/*

# Copy project files
COPY pyproject.toml uv.lock alembic.ini README.md ./
COPY quantshark_shared/ ./quantshark_shared/

# Install dependencies
RUN uv sync --frozen --no-dev

ENV PATH="/app/.venv/bin:$PATH"

# Default command
CMD ["alembic", "upgrade", "head"]
