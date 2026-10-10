# AGENTS.md

## Project Overview

Minimal Node.js web app (Base Code E2E test fixture). Single file `server.js` — no dependencies, no database, no external services.

## Setup

- Runtime: Node.js >= 20 (no `npm install` needed — only uses Node built-ins).
- Start: `node server.js` (or `node --watch server.js` for live reload).
- Listens on `PORT` env var (default 3000), binds to `::` (all interfaces).

## Verification

- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Constraints

The README says: do not change the app content — E2E tests depend on its exact output.
