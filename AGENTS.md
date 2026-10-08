# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 (binds `::` so IPv4+IPv6).
- No build step, no migrations, no seeds.

## Live Reload
The app is a plain `node server.js` process with no dev server or file watcher. After code changes, call `reload_preview` so the user sees them (or restart the `web` service).

## Constraints
- README warns: "Please don't change it: the tests depend on its exact content." Avoid modifying `server.js`, `package.json`, or `Dockerfile` beyond what is needed to run in this environment.
