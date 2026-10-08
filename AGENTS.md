# AGENTS.md

## Project

Minimal Node.js web app (single file `server.js`, no dependencies, no database, no external services).

## Running

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- App listens on port 3000.
- `GET /` serves the HTML page; `GET /health` returns `{"status":"ok"}`.
- No live-reload dev server — plain `node server.js`. After editing `server.js`, restart the `app` service or call `reload_preview`.

## Notes

- The README says tests depend on exact content of `server.js` and `package.json` — avoid changing them.
- No secrets or environment variables are required.
