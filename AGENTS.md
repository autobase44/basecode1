# Base44 Setup Notes

This is a minimal Node.js app (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App serves on port 3000; `GET /` shows the page, `GET /health` returns `{"status":"ok"}`.
- Runs from bind-mounted source via `node server.js` (no live-reload; call `reload_preview` after edits).

## No secrets required
The app has no environment variables beyond `PORT` and needs no external credentials.
