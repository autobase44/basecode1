# Setup notes (Base44 sandbox)

`base-code-e2e` is a zero-dependency Node HTTP fixture. `server.js` serves `/`
(HTML heading "Base Code E2E") and `/health` (`{"status":"ok"}`).

## Run it

```
docker compose -f docker-compose.base44.yml up -d --build
```

- Runs the source bind-mounted into a plain `node:22-alpine` service, *not* the
  repo `Dockerfile` (that COPYs source into an image, which would freeze edits).
- No dependencies, no env vars, no database, no migrations, no secrets.
- `server.js` calls `listen(PORT)` with no host, so it binds all interfaces; no
  bind-address or host-allowlist override is needed for the preview proxy.
- The project has no live-reload runner and no dependencies to add one, so the
  service runs `node server.js` directly. After an edit, restart the service
  (`docker compose -f docker-compose.base44.yml restart web`) and reload the preview.

## Verify

```
curl -s http://localhost:3000/health   # -> {"status":"ok"}
curl -s http://localhost:3000/ | grep 'e2e-marker'
```

Compose healthcheck probes `/health` via node's built-in `http` module (the
alpine image has no curl).

Do not change `server.js`/`package.json` content: external E2E tests assert it.
