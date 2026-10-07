# AGENTS.md

Notes for running this repo in the Base44 sandbox.

## Running

Use the Base44 dev compose file, not the repo's own Dockerfile:

```
docker compose -f docker-compose.base44.yml up -d
```

## Why not the repo's Dockerfile

`Dockerfile` does `COPY package.json server.js ./` — it bakes the source into a
production image. Running from it would freeze the code and make every edit
invisible in the preview. `docker-compose.base44.yml` instead uses a plain
`node:20-alpine` image, bind-mounts the repo at `/app`, and runs `node server.js`
directly, so edits to `server.js` take effect on the next container restart.

## No dev server / live reload

`server.js` is a plain Node HTTP server with no watcher. After changing source,
restart the service (`docker compose -f docker-compose.base44.yml restart web`)
or reload the preview.

## Requirements

None. No npm dependencies (`npm install` is a no-op), no database, no environment
variables, no external services or credentials.

## Verifying

- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → page whose heading is "Base Code E2E"
- Compose healthcheck probes `/health`.

## Caution

The README asks that this fixture's exact content not be changed: Base44's own
end-to-end tests depend on it.
