# Base44 Setup Notes

## Project Overview
Minimal Node.js web app (no dependencies, no database, no environment variables).
Single `server.js` file using only `node:http`. Serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 inside the container (mapped to host 3000).
- No `npm install` needed — zero dependencies.
- No live-reload dev server; use `reload_preview` after editing `server.js`.

## Health Check
- `GET /health` returns `{"status":"ok"}`

## Constraints
- README says: "Please don't change it: the tests depend on its exact content."
  Do not modify `server.js` or `package.json` unless explicitly asked.
