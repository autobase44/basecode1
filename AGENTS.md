# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Serves an HTML page at `/` and a JSON health check at `/health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d
```
- Web service runs from cloned source (`server.js`) via `nodemon` for live reload.
- Exposed on host port 3000.
- Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- No environment variables or secrets required.
- The README states the app is a test fixture — do not change `server.js`, `package.json`, or `Dockerfile` content as tests depend on exact content.
- `nodemon` is installed at container startup (not a project dependency) to provide live reload without modifying `package.json`.
