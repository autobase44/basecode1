# Agent notes

## What this app is
A minimal Node.js HTTP fixture (no dependencies, no database, no environment
variables) used by Base44 Base Code E2E tests. Do not change `server.js`,
`package.json`, or the Dockerfile — the tests depend on their exact content.

## Running it here (Base44 sandbox)
Use `docker-compose.base44.yml`, NOT the repo's own `Dockerfile` (that is a
production-style image and cannot reflect edits):

```
docker compose -f docker-compose.base44.yml up -d --build
```

- The app runs from the bind-mounted source (`./:/app`) on `node:20-alpine`
  with `node --watch server.js`, so file edits restart the server without an
  image rebuild.
- Web entry point: host port 3000.
- No install step is needed (there are no runtime dependencies).

## Verifying it works
- `curl http://localhost:3000/` → HTML page whose heading is "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

The compose healthcheck probes `/health` so `docker compose ps` shows the
`web` service as healthy once the server is up.
