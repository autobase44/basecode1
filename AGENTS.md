# base-code-e2e — sandbox notes

Test fixture for Base44 Base Code E2E tests. Its content is depended on: do not
change `server.js`, `package.json` or `Dockerfile`.

## Running it here

- `docker compose -f docker-compose.base44.yml up -d` — single `web` service.
- The service runs `node --watch server.js` from the bind-mounted repo, **not**
  the repo's own `Dockerfile`. That Dockerfile `COPY`s the source into a
  prebuilt image, so it cannot show edits; it is only used for standalone
  `docker build` / `docker run` use.
- No dependencies, no database, no environment variables, no secrets. Do not add
  `env_file: /run/base44/app.env` — the app has nothing to read from it.
- `node --watch` is Node's built-in watcher and provides live reload with no
  added dev dependency, so the fixture's "no dependencies" property is preserved.

## Verifying

- `curl -fsS http://localhost:3000/health` → `{"status":"ok"}`
- `curl -fsS http://localhost:3000/` → page containing `data-testid="e2e-marker"`
  and the heading `Base Code E2E`.
- Live reload check without editing content: `touch server.js`, then the logs
  should show `Restarting 'server.js'` followed by `Listening on 3000`.
