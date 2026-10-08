# Base44 Dev Environment

## Overview

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no
external services. Serves a static HTML page at `/` and a JSON health check at
`/health` on port 3000.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

The compose file uses a plain `node:20-alpine` image with the repo bind-mounted
at `/app`, so source edits are picked up on container restart. There is no
framework HMR; call `reload_preview` after editing `server.js`.

## Health Check

`GET /health` → `{"status":"ok"}`

## Notes

- The README asks not to change the app content — the E2E test fixture depends
  on the exact heading "Base Code E2E".
- No environment variables or secrets are required.
