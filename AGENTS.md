# Base44 Dev Environment

## Project

Minimal Node.js web app (`server.js`) — no dependencies, no database, no external services.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- App listens on port 3000, serves HTML at `/` and JSON at `/health`.
- No live-reload dev server; `node server.js` runs directly. Call `reload_preview` after edits.
- No environment variables or secrets required.

## Verification

- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
