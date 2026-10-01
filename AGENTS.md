# Base44 Dev Environment

## Project
Minimal Node.js web app (`server.js`) with zero dependencies, no database, no environment variables.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Notes
- No live-reload dev server; `node server.js` is the only command. Call `reload_preview` after edits.
- No secrets or external services required.
- Source is bind-mounted; no image rebuild needed for code changes.
