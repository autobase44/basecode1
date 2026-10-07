# Base44 Dev Environment

This is a minimal Node.js web app (single `server.js`, no dependencies, no database, no external services).

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- The app listens on port 3000.
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.
- Source is bind-mounted; `node --watch` provides live reload on file changes.
- No environment variables or secrets are required.
