# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Used as an E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves HTML at `/`, JSON at `/health`.
- Source is bind-mounted into the container; there is no live-reload dev server, so code changes require a container restart (`docker compose -f docker-compose.base44.yml restart web`).

## Health
- `GET /health` returns `{"status":"ok"}`.

## Secrets
- None required.
