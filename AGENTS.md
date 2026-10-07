# Base44 sandbox notes

Test fixture app. The README asks that `server.js`, `package.json`, and `Dockerfile`
keep their exact content because the E2E tests depend on it — do not edit them.

## Running here

- `docker compose -f docker-compose.base44.yml up -d --build` serves the app on host port 3000.
- The service runs `node --watch server.js` from the bind-mounted source, so edits to
  `server.js` restart the server automatically (no image rebuild).
- No dependencies, environment variables, or database are required.

## Verifying

- `curl -s http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/` → HTML page with the `data-testid="e2e-marker"` heading "Base Code E2E".
