# Base44 Dev Environment

Minimal Node.js HTTP app (`server.js`), no dependencies, no database, no environment variables.

- Run: `docker compose -f docker-compose.base44.yml up -d`
- Preview: host port 3000 → `GET /` shows the "Base Code E2E" page; `GET /health` returns `{"status":"ok"}`.
- No live-reload dev server (`node server.js`); call `reload_preview` after edits to `server.js`.
- This repo is an E2E test fixture — avoid changing app behavior beyond what is requested.
