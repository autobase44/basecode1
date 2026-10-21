# Base44 sandbox notes

## What this project is
`base-code-e2e` is a fixture app used by Base44 Base Code E2E tests. The README asks
that its content not be changed (the tests assert on the exact page). Keep edits to
the sandbox setup files, not to `server.js` / `package.json`.

## Running it here
```sh
docker compose -f docker-compose.base44.yml up -d
```
- Single service `web` on host port 3000, running `node --watch server.js` from the
  bind-mounted checkout (`node --watch` is built into Node 20+, so no extra dep).
- No dependencies to install, no database, no migrations, no environment variables
  and no secrets. Do not add a repo-root `.env`.

## Verifying it works
```sh
curl -fsS http://localhost:3000/health   # -> {"status":"ok"}
curl -fsS http://localhost:3000/          # -> HTML containing data-testid="e2e-marker"
```
Compose healthcheck probes `/health` with busybox `wget` (present in the alpine image).

## Notes
- `server.js` calls `listen(PORT)` without a host, which binds `::` (IPv4 + IPv6), so
  `127.0.0.1` / `localhost` probes both work — no bind-address override needed.
- Live reload: the `node --watch` process restarts on `server.js` changes. A compose
  or command change (not source) needs `docker compose -f docker-compose.base44.yml up -d`.
