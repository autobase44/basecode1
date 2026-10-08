# Base44 dev environment notes

Minimal Node app with **no dependencies, no environment variables, no database**.
Do not add a package install step — `package.json` has no dependencies.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

Serves on host port 3000 via a `node:20-alpine` container with the repo bind-mounted
at `/app`, started with `node --watch server.js` (auto-restart on file change).

## Verifying

- `curl -s http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/` → HTML page with heading `Base Code E2E`

## Notes

- `server.js` binds without an explicit host so it accepts connections on all
  interfaces — required for the sandbox preview proxy.
- The repo README asks that the app content stay byte-exact (it is a fixture for
  Base Code E2E tests), so the sandbox setup is confined to compose/config files
  and does not touch `server.js`, `package.json`, or `Dockerfile`.
