# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services. Serves a static HTML page at `/` and JSON health at `/health` on port 3000.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app with `node --watch` (live reload on file changes).
- Preview port: 3000. Health path: `/health`.
- No environment variables or secrets required.

## Notes
- The README says tests depend on exact content — avoid changing `server.js` or `README.md` unless explicitly asked.
- `node --watch` provides live reload; no nodemon or extra dev dependency needed.
