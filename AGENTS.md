# AGENTS.md

## Project overview

Minimal Node.js web app (test fixture). Single file `server.js` using only `node:http` — no dependencies, no database, no external services.

- `npm start` runs `node server.js`, serving on port 3000.
- `GET /` returns an HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Running in the sandbox

```
docker compose -f docker-compose.base44.yml up -d --build
```

The compose file uses `node:20-alpine` with the source bind-mounted at `/app`. No live-reload dev server exists (the app is plain `node server.js`); call `reload_preview` after code changes.

## Verification

- `curl http://localhost:3000/` should return HTML containing "Base Code E2E".
- `curl http://localhost:3000/health` should return `{"status":"ok"}`.
