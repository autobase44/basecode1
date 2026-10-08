# Base Code E2E — Base44 Setup Notes

## What this is
A minimal single-file Node.js web app (`server.js`) used as an E2E test fixture. No dependencies, no database, no environment variables required.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d --build`
- The app listens on port 3000 and serves `/` (HTML page) and `/health` (JSON `{"status":"ok"}`).
- Uses `node:20-alpine` base image with source bind-mounted — no image rebuild needed for edits.
- No live-reload dev server (the app is a plain `http.createServer`); call `reload_preview` after code changes.

## Verification
- `curl http://localhost:3000/` → HTML with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## No secrets needed
The app has no external service dependencies.
