# Base44 dev notes — base-code-e2e

Minimal Node.js fixture app. Single file `server.js`, no dependencies, no database, no environment variables.

## Run
```
docker compose -f docker-compose.base44.yml up -d --build
```
App listens on port 3000. `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Live reload
Uses Node's built-in `--watch` flag (`node --watch server.js`) — edits to `server.js` restart the server automatically. No dev server or extra dependency required.

## Caveats
- The README asks not to change the app's content (E2E tests depend on the exact heading "Base Code E2E").
- `package.json` has no dependencies, so no install step is needed.
