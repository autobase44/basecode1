# Base44 Dev Environment

## App overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services.
- `GET /` returns an HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 inside the container.
- Live reload via `nodemon` (installed at container start); edits to `server.js` restart the server automatically.

## Notes
- No environment variables or secrets required.
- The README says not to change app content — tests depend on exact page text.
