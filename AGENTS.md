# Base44 Setup Notes

## Project Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database). Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` base image with source bind-mounted at `/app`.
- No live-reload (plain `node server.js`); call `reload_preview` after edits.
- Health check: `GET /health` → `{"status":"ok"}`

## No Secrets Required
The app has no environment variables, no external services, and no database.
