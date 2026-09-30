# Base44 Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no env vars). Single file: `server.js`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: port 3000 → `GET /` (HTML page)
- Health check: `GET /health` → `{"status":"ok"}`
- Live reload via nodemon (installed globally in the container, not added to the repo).

## Important
The README says: "Please don't change it: the tests depend on its exact content." Do not modify `server.js` or `package.json` unless explicitly asked — the E2E test fixture depends on their exact content.
