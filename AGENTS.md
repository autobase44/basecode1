# Base44 Dev Environment

Minimal Node.js HTTP server (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in, no extra deps).
- Source is bind-mounted, so edits appear without rebuilding the image.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck: `wget -qO- http://localhost:3000/health`.

## Notes
- No environment variables or secrets required.
- The README says not to change this app — it's a test fixture.
