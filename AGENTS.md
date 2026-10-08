# Base44 Setup Notes

## Project

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d
```

- App listens on port 3000, serves `GET /` (HTML page) and `GET /health` (JSON `{"status":"ok"}`).
- Source is bind-mounted; there is no live-reload dev server, so call `reload_preview` after edits.
- No environment variables or secrets required.
