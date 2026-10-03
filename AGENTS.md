# Base44 Dev Environment

## Project
Minimal Node.js web app (no dependencies, no database, no env vars). Single `server.js` using `node:http`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- App runs from bind-mounted source at `/app` using `node --watch` (live reload on file changes).
- Web entry point on host port 3000.
- `GET /` → HTML page; `GET /health` → `{"status":"ok"}`.

## Notes
- No `npm install` needed — zero dependencies.
- No external credentials required.
- Node 20+ built-in `--watch` flag provides live reload without nodemon.
