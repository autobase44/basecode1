# Base44 Dev Environment

Minimal Node.js HTTP server fixture (`server.js`). No dependencies, no environment variables, no database.

## Run
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: host port 3000 -> container 3000.
- Healthcheck: `GET /health` -> `{"status":"ok"}`.
- Source is bind-mounted at `/app`; the container runs `node server.js` directly (no build step, no live-reload). After editing `server.js`, restart the service or call `reload_preview`.

## Notes
- No `node_modules` or lockfile — `package.json` has zero dependencies.
- No external credentials required.
