# Base44 Dev Environment

## Overview

Minimal Node.js web app (no dependencies, no database, no env vars). A single `server.js` serves HTML on `/` and JSON on `/health`.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d
```

- App runs from bind-mounted source via `node --watch server.js` (live reload on file changes).
- Web entry point on host port 3000.
- Health check: `GET /health` → `{"status":"ok"}`.

## Notes

- No `npm install` needed — zero dependencies.
- No external secrets or credentials required.
