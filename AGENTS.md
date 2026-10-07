# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (`server.js`) with **no dependencies, no database, no external services**.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts on port 3000.
- The app is a plain `http.createServer` (no framework dev server), so edits require `reload_preview` to appear in the preview.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.
- Main page: `GET /` returns the HTML page with heading "Base Code E2E".
