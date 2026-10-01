# Base44 Dev Environment

## Project

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no environment variables, and no database. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running

```
docker compose -f docker-compose.base44.yml up -d --build
```

The app listens on port 3000 (mapped to host port 3000).

## Notes

- No live-reload dev server: `node server.js` is a plain HTTP server. After editing `server.js`, restart the container (`docker compose -f docker-compose.base44.yml restart web`) or call `reload_preview`.
- The README asks not to change the app content — the E2E test fixture depends on exact output.
- No secrets or external services required.
