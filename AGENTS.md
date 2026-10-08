# Base44 Dev Environment

## Overview

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

The app listens on port 3000. Healthcheck uses `GET /health` → `{"status":"ok"}`.

## Notes

- No live-reload dev server (plain `node server.js`). After editing `server.js`, call `reload_preview` so the user sees the change.
- No secrets or external services required.
- The repo is an E2E test fixture — avoid changing `server.js` or `package.json` content that tests depend on.
