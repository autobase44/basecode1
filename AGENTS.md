# AGENTS.md

## Project Overview

Minimal Node.js web app (single `server.js` file, zero npm dependencies). Serves a static HTML page at `/` and a JSON health check at `/health` on port 3000.

## Setup

- No dependencies to install — `package.json` has no `dependencies`.
- No environment variables, no database, no external services.
- Run via `docker compose -f docker-compose.base44.yml up -d`.

## Dev Notes

- The app has no live-reload dev server (plain `node server.js`). After editing `server.js`, call `reload_preview` so the user sees the change.
- The Dockerfile in the repo bakes source via `COPY`; the Base44 compose uses a plain `node:20-alpine` image with the source bind-mounted instead, so edits are picked up on container restart.
