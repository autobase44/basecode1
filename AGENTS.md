# Base44 environment notes

Non-obvious things about running this repo in the Base44 sandbox. See `README.md`
for what the app itself is, and `docker-compose.base44.yml` for the executable
runbook.

## What it needs
Nothing beyond Node. No dependencies (`package.json` has no `dependencies`), no
lockfile, no database, no environment variables.

## How it runs here
- `docker compose -f docker-compose.base44.yml up -d --build` starts a single
  `web` service (`node:20-alpine`) with the repo bind-mounted at `/app`.
- The service runs `node --watch server.js`, so editing `server.js` reloads the
  server in place — no rebuild, no restart needed.
- The repo's own `Dockerfile` is **not** used: it `COPY`s the source into an
  image, which would freeze the code and break the edit loop. Do not switch the
  compose service to `build:` that Dockerfile.
- Healthcheck probes `GET /health` from inside the container; `depends_on`
  graphs would key off `service_healthy` if more services are added.

## Verifying it works
- `curl -s localhost:3000/health` → `{"status":"ok"}`
- `curl -s localhost:3000/` → HTML containing `Base Code E2E`

## Do not change the app
`README.md` states the tests depend on its exact content — treat `server.js`'s
markup, `GET /health` response and the `data-testid="e2e-marker"` heading as a
fixed contract.
