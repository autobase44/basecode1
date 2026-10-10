# AGENTS.md

## Project Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup
- No `npm install` needed — `package.json` has no dependencies.
- No database, no external services, no environment variables required.
- Run via `docker compose -f docker-compose.base44.yml up -d`.
- The app listens on port 3000 (configurable via `PORT` env var).

## Development Notes
- This is a raw `node` HTTP server with no live-reload framework. After editing `server.js`, call `reload_preview` to see changes.
- Source is bind-mounted into the container, so edits are reflected on container restart.
- The README states the tests depend on exact content — do not change the page content.
