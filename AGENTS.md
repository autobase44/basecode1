# AGENTS.md

## Overview

Minimal Node.js web app (single `server.js`) used as a Base44 E2E test fixture.
No dependencies, no environment variables, no database.

## Running

- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, serves HTML at `/` and JSON at `/health`.
- Uses `node --watch` for live reload on file changes (bind-mounted source).

## Notes

- Do not change the page content — E2E tests depend on the exact heading "Base Code E2E".
- No external credentials required.
