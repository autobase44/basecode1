# Base44 sandbox notes

Minimal Node HTTP app (`server.js`, no dependencies). The README asks that its
exact content be preserved — the Base44 Base Code E2E tests depend on it.

## Running here

```bash
docker compose -f docker-compose.base44.yml up -d --build
curl http://localhost:3000/        # HTML page, heading "Base Code E2E"
curl http://localhost:3000/health  # {"status":"ok"}
```

- The compose file bind-mounts the repo into `node:20-alpine` and runs
  `node --watch server.js`, so edits to `server.js` reload in place — no rebuild
  needed. Restart the service only after changing compose itself.
- No dependencies, no environment variables, no database, no secrets.
- There is no separate dev/test/lint toolchain; the only runtime check is
  `GET /`.
