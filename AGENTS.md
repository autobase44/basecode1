# AGENTS.md

## Project overview

Minimal Node.js web app (Base44 Base Code E2E test fixture). No dependencies, no database, no environment variables.

- Entry point: `server.js` (plain `node:http`, no framework)
- `GET /` serves the HTML page (heading "Base Code E2E")
- `GET /health` returns `{"status":"ok"}`

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

The compose service uses `node:20-alpine` with the repo bind-mounted at `/app` and runs `node server.js`. Port 3000 is the web entry point.

## Notes

- There is no live-reload dev server (plain `node server.js`); call `reload_preview` after editing `server.js` for changes to appear.
- The README states tests depend on exact content — do not change the source files unless explicitly asked.
