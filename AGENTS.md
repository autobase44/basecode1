# AGENTS.md

## Overview

Minimal Node.js web app (`server.js`) used as a Base44 Base Code E2E test fixture.
No dependencies, no environment variables, no database.

## Running

```
docker compose -f docker-compose.base44.yml up -d
```

- Web entry point: `http://localhost:3000/` (heading "Base Code E2E")
- Health check: `GET /health` → `{"status":"ok"}`

## Editing

The app is a raw `http.createServer` with no live-reload dev server. After
editing `server.js`, restart the service to see changes:

```
docker compose -f docker-compose.base44.yml restart web
```

Then call `reload_preview` to refresh the preview iframe.

## Notes

- Do not change the page content or endpoints — E2E tests depend on exact output.
- The server binds all interfaces (no explicit host) so it accepts the preview's external hostname.
