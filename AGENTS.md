# AGENTS.md — base-code-e2e

Minimal Node HTTP server fixture. Findings that aren't obvious from the manifests:

- **Do not change `server.js` or the page content.** The README says so explicitly:
  the Base44 Base Code E2E tests assert on the exact heading `Base Code E2E`
  (`data-testid="e2e-marker"`) and on `GET /health` returning `{"status":"ok"}`.
- **Do not run the repo's own `Dockerfile`.** It `COPY`s `package.json server.js`
  into the image at build time, so edits would never reach the preview. The
  sandbox setup (`docker-compose.base44.yml`) bind-mounts the repo instead and
  runs `node --watch server.js`.
- No dependencies, no env vars, no database, no external services → no secrets
  and no migration/seed step.
- `server.js` ignores the request path except `/health`, which it answers before
  anything else; every other path returns the same HTML page.
- `listen(PORT)` is called without a host, so it binds dual-stack `::` — a
  `localhost` healthcheck works over IPv4 or IPv6.

## Verify it works

```sh
docker compose -f docker-compose.base44.yml up -d
curl -s http://localhost:3000/health        # {"status":"ok"}
curl -s http://localhost:3000/ | grep 'Base Code E2E'
```

If you ever add npm dependencies, add a non-interactive, lockfile-preserving
install step to the `web` service's `command:` before `exec node --watch server.js`
(the bind-mounted `/app` has no `node_modules` of its own).
