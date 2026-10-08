# Base44 Setup Notes

## Project
Minimal Node.js web app (single `server.js`, no dependencies, no database, no env vars).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App binds port 3000, serves `GET /` (HTML page) and `GET /health` (JSON `{"status":"ok"}`).
- Source is bind-mounted; the app has no live-reload dev server, so call `reload_preview` after edits.

## Notes
- The README says the app is a test fixture — avoid changing `server.js` content unless asked.
- No secrets or external credentials required.
