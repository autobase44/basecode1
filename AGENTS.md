# Base44 Setup Notes

Minimal Node.js fixture app — no dependencies, no database, no environment variables required.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

- Base image: `node:20-alpine` (plain runtime, source bind-mounted at `/app`).
- Dev command: `node --watch server.js` — Node's built-in file watcher restarts on edits, no extra dependency needed.
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Verification

- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
