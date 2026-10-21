# Working in this repo

Minimal Node HTTP server fixture. See README.md — its content is deliberate and
the Base44 E2E tests depend on it, so avoid changing `server.js` output.

## Running it here (Base44 sandbox)

```bash
docker compose -f docker-compose.base44.yml up -d
```

- Single service `web` on host port 3000: `node:22-alpine` running
  `node --watch server.js` with the repo bind-mounted at `/app`.
- Do NOT use the repo's `Dockerfile` for the sandbox: it `COPY`s the source into
  the image, so edits would not reach the preview. The Base44 compose runs the
  cloned source directly instead.
- There are **no dependencies** (`package.json` has none) and **no environment
  variables or secrets**, so no install step and no `env_file` are needed. No
  host/origin allowlist either: the server does not inspect `Host`, and
  `BASE44_PREVIEW_MODE` is therefore unnecessary here.

## Verify

- `curl -s localhost:3000/` → HTML page with the `Base Code E2E` heading.
- `curl -s localhost:3000/health` → `{"status":"ok"}` (also the compose
  healthcheck).
- Live reload: `node --watch` restarts on save, so source edits appear without a
  rebuild. If a change still doesn't show, reload the preview.
