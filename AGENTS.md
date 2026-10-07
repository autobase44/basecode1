# Base44 Setup Notes

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point: host port 3000 → container 3000.
- Health check: `GET /health` returns `{"status":"ok"}`.
- Live reload via `nodemon` watching `server.js`.

## Notes
- The README says not to change `server.js` or `package.json` — E2E tests depend on their exact content.
- No external credentials or secrets are needed.
