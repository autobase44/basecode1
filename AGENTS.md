# AGENTS.md

## Overview

Minimal Node.js HTTP server fixture (`server.js`) with zero dependencies. Serves an HTML page at `/` and a JSON health check at `/health`.

## Running in the Base44 sandbox

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- Base image: `node:20-alpine` (plain runtime; source is bind-mounted, not baked in).
- Live reload: `node --watch server.js` (Node 20+ built-in watch mode — no extra dependency needed).
- Web entry point: host port 3000.
- Health check: `GET /health` returns `{"status":"ok"}`.
- No environment variables, no database, no external credentials required.
