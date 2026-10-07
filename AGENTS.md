# Base44 Dev Environment

This is a minimal Node.js fixture app (`base-code-e2e`) with no dependencies, no environment variables, and no database. The README instructs not to change the app content — the Base44 E2E tests depend on its exact output.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d
```

- Web entry point: `http://localhost:3000` (mapped from container port 3000).
- Health check: `GET /health` returns `{"status":"ok"}`.
- The source is bind-mounted and the container runs `node --watch server.js`, so edits to `server.js` hot-reload without a rebuild.
- No secrets or external credentials are required.
