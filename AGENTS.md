# Working in this repo (Base44 sandbox notes)

`base-code-e2e` is a **fixture**: the Base44 Base Code E2E tests depend on its exact
content (heading `Base Code E2E`, `data-testid="e2e-marker"`, `GET /health` →
`{"status":"ok"}`). Treat `server.js`, `package.json`, `README.md` and `Dockerfile`
as read-only unless a change to the fixture is explicitly requested.

## Run it here

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- One service, `web`, on host port 3000 (the preview entry point).
- Plain `node:22-alpine`, source bind-mounted at `/app`; nothing is baked into an
  image. The repo has **no dependencies**, no database, no migrations, no seeds and
  **no environment variables or secrets** — so there is nothing to install or
  configure before boot.
- The repo's own `Dockerfile` is intentionally not used by the compose file: it
  `COPY`s the source into an image, which would freeze the code and break the edit
  loop. It remains correct for the standalone `docker build && docker run` flow in
  the README.

## Non-obvious quirk: don't go back to `node --watch`

`node --watch` is **not** reliable for this bind mount. It follows the file
*inode*, and the usual "write a temp file, rename it over the target" save leaves
the watcher pointing at the unlinked inode, so only the first edit reloads and
later ones are silently ignored (verified: 1 of 3 saves reloaded; the served page
kept the stale text). The compose file therefore runs an inline polling supervisor
(re-stats `server.js` every 500ms) which reloads on every write style, and also
respawns the app if it exits while a broken file is being fixed.

If a change ever fails to appear, reload the preview and check
`docker compose -f docker-compose.base44.yml logs web` for `[dev] change detected`.

## Verify it works

```bash
curl -sS http://localhost:3000/ | grep -o '>Base Code E2E<'   # page renders
curl -sS http://localhost:3000/health                          # {"status":"ok"}
docker compose -f docker-compose.base44.yml ps                 # web = healthy
```

The compose healthcheck probes `/health` over HTTP, so it fails if the app itself is
down, not merely if the supervisor process is alive. There is no test suite in the
repo; the CI tests that depend on this fixture live in the Base44 repo.

## Preview notes

The app is server-rendered with **no client-side router** — every path returns the
same HTML. Preview `navigate()` (SPA pushState) will report that the route did not
render; assert on the loaded document instead.
