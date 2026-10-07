# Base44 dev environment

This is a minimal, dependency-free Node.js HTTP fixture app (`server.js`) with no
environment variables, no database, and no external services.

## Running in the sandbox

```
docker compose -f docker-compose.base44.yml up -d --build
```

- The app runs from the bind-mounted source (`./` → `/app`) using `node --watch server.js`,
  so edits to `server.js` hot-reload without a rebuild.
- Web entry point is on host port 3000.
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}` (used by the compose healthcheck).
- No secrets or credentials are required.

## Notes

- The repo's own `Dockerfile` bakes source via `COPY` (production-style); the Base44
  compose intentionally does NOT use it, so live edits stay visible in the preview.
- The README asks not to change the app's content (E2E tests depend on it); Base44
  setup only adds `docker-compose.base44.yml`, `.base44/`, and this file.
