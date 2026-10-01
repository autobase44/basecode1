# AGENTS.md

## Project Overview

Minimal Node.js web app (Base Code E2E test fixture). No dependencies, no database, no external services.

## Setup

- Runtime: Node.js >= 20 (compose uses `node:22-alpine`)
- No `npm install` needed — the app has zero dependencies.
- Dev command: `node --watch server.js` (built-in file watcher, restarts on edit).
- Serves on port 3000: `GET /` returns the HTML page, `GET /health` returns `{"status":"ok"}`.

## Verification

- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Constraints

- The README says: "Please don't change it: the tests depend on its exact content." Avoid modifying `server.js` or `package.json` unless explicitly asked.
