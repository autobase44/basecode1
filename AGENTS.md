# Base44 Setup Notes

## Project
Minimal Node.js web app (`server.js`) — no dependencies, no env vars, no database.

## Running
`docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E"
- `GET /health` returns `{"status":"ok"}`

## Notes
- No live-reload dev server; `node server.js` serves directly. Call `reload_preview` after code changes.
- No external secrets or credentials needed.
