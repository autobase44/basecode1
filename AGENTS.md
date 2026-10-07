# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`), no dependencies, no env vars, no database.
Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App is served on host port 3000. Source is bind-mounted; restart the `web` service
(or `reload_preview`) after edits — there is no live-reload watcher.

## Notes
- The README asks not to change the app content (E2E test fixture depends on it).
- No secrets or external services required.
