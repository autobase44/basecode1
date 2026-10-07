# AGENTS.md — Base44 sandbox notes

Minimal Node HTTP fixture (see README: its exact content is depended on by Base44 E2E tests —
avoid changing `server.js`, `package.json` or `Dockerfile`).

## Running in the Base44 sandbox

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- The repo's own `Dockerfile` is a production build (`COPY package.json server.js ./`), so it
  freezes the code — do NOT use it for the sandbox. `docker-compose.base44.yml` runs the source
  bind-mounted into a plain `node:20-alpine` image instead.
- Live reload comes from Node's built-in watcher: `node --watch server.js`. No dependency install
  is needed — the app has no packages, no database and no environment variables beyond `PORT`.
- Web entry point: host port `3000` (`/` page, `/health` JSON healthcheck).

## Verifying it works

```bash
curl -s http://localhost:3000/health          # {"status":"ok"}
curl -s http://localhost:3000/ | grep e2e-marker   # heading "Base Code E2E"
docker compose -f docker-compose.base44.yml ps     # web should be "healthy"
```
