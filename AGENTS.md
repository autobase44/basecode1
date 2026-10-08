# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no external services. Serves a static page at `/` and a health check at `/health`.

## Setup
- Runs via `docker-compose.base44.yml` using the `node:20-alpine` base image with the source bind-mounted at `/app`.
- No `npm install` needed — the app uses only Node's built-in `http` module.
- No live-reload dev server; after editing `server.js`, call `reload_preview` so the change is visible. (The README explicitly says not to add dependencies, so nodemon is not used.)
- No environment variables or secrets are required.

## Verification
- `curl http://localhost:3000/health` returns `{"status":"ok"}`
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E"
