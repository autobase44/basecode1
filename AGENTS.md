# Base44 Setup Notes

## Project Overview

Minimal Node.js web app (single file: `server.js`) used as a Base44 E2E test fixture.
No dependencies, no database, no external services, no environment variables required.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

- App listens on port 3000.
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes

- The app has no live-reload dev server (no nodemon/vite). After editing `server.js`, call `reload_preview` or restart the service: `docker compose -f docker-compose.base44.yml restart app`.
- Source is bind-mounted at `/app`, so file changes are visible in the container immediately; only the Node process needs a restart to pick them up.
- No secrets or external credentials are needed.
