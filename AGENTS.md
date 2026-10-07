# Base44 sandbox notes — base-code-e2e

Minimal Node HTTP fixture. See `README.md` for what the app is; the repo's own
`Dockerfile` bakes `server.js` into the image, so do **not** use it for sandbox
runs — use `docker-compose.base44.yml`, which runs `node server.js` from the
bind-mounted source.

## Bring up / verify

```
docker compose -f docker-compose.base44.yml up -d --build
curl -s http://localhost:3000/health   # {"status":"ok"}
curl -s http://localhost:3000/ | grep 'Base Code E2E'
```

Health endpoint is `/health`; the preview entry point is host port 3000.

## Notes

- No dependencies, no lockfile, no `node_modules` — nothing to install at startup.
- No environment variables and no external services, so no secrets required.
- There is no live-reload dev server (`npm start` just runs `node server.js`);
  after editing `server.js`, call `reload_preview` (or restart the `app` service)
  so the change is reflected.
- The app listens on `PORT` (default 3000) on all interfaces — no host-binding
  config needed for the preview proxy.
- This repo is an E2E test fixture; its content is expected to stay stable.
