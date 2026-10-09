# AGENTS.md

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database). Used as a Base44 E2E test fixture.

## Setup
- Runtime: Node 20 (via `node:20-alpine` in `docker-compose.base44.yml`)
- Source is bind-mounted; `node --watch server.js` provides live reload on edits
- No `npm install` needed — zero dependencies
- No environment variables or external credentials required

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
- Healthcheck: `wget -qO- http://localhost:3000/health`
