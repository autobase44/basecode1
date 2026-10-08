# AGENTS.md

## Running here (Base44 sandbox)

- Use `docker compose -f docker-compose.base44.yml up -d`; the page is served on host port 3000.
- Do **not** run the repo `Dockerfile` for sandbox work: it `COPY`s `package.json` and `server.js`
  into the image, so edits would never show. The Base44 compose runs `node --watch server.js`
  from the repo bind-mounted at `/app` instead.
- The app has zero dependencies, no lockfile, no env vars, and no database — nothing to install,
  migrate, or seed. `node:20-alpine` is the only image needed.

## Verifying it works

- `curl -s http://localhost:3000/health` → `{"status":"ok"}` (also the compose healthcheck).
- `curl -s http://localhost:3000/` → HTML containing `data-testid="e2e-marker"` and the heading
  "Base Code E2E".
- Edits to `server.js` are picked up by Node's built-in watcher; `docker compose logs -f web`
  prints `Restarting 'server.js'` on reload.

## Notes

- This repo is a fixture for Base44 Base Code E2E tests and the tests depend on its exact content
  (heading text, `data-testid`, `/health` payload). Avoid changing app behavior or markup.
