# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Test fixture for Base44 Base Code E2E tests. **Do not modify `server.js`, `Dockerfile`, `package.json`, or `README.md`** — the E2E tests depend on their exact content.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- App listens on port 3000.
- `GET /` → HTML page with heading "Base Code E2E".
- `GET /health` → `{"status":"ok"}`.

## Notes
- No live-reload dev server; the app is plain `node server.js`. Source is bind-mounted, but changes require a container restart (`docker compose -f docker-compose.base44.yml restart web`) or `reload_preview`.
- No secrets or external services required.
