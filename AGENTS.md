# Base44 Setup Notes

## Project Overview
Minimal Node.js app (`server.js`) serving a single HTML page. No dependencies, no database, no external services.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- App listens on port 3000.
- Health check at `/health` returns `{"status":"ok"}`.
- Source is bind-mounted; no live-reload — call `reload_preview` after edits.

## No Secrets Required
This project needs no external credentials.
