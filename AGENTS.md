# AGENTS.md

## Overview

Minimal Node.js web app (single `server.js`, no dependencies, no database, no env vars).
Used as a fixture by Base44 Base Code E2E tests — the tests depend on its exact content.

## Running

- `docker compose -f docker-compose.base44.yml up -d`
- Uses `node --watch server.js` for live reload on file changes.
- Web entry point on port 3000; health check at `GET /health` → `{"status":"ok"}`.
- No secrets or external credentials required.
