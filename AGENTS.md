# Base44 Setup Notes

## Project
Minimal zero-dependency Node.js web app (`server.js`) used as a Base44 E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves HTML at `/` and JSON at `/health`.
- No dependencies, no environment variables, no database, no external secrets.

## Live reload
- Uses `nodemon` (installed on container startup, not saved to package.json) to watch `server.js`.
- No other files need watching; the entire app is a single file.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
