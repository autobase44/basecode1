# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Dev mode
- Source is bind-mounted; `nodemon` watches `server.js` for live reload.
- No `npm install` needed (zero dependencies in `package.json`).

## No secrets required
The app has no environment variables, API keys, or database connections.
