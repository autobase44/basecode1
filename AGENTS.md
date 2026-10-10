# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (no framework, no dependencies, no database). Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20+ built-in watch mode).
- No dependencies to install — the app uses only Node built-ins.
- No environment variables or external credentials required.
