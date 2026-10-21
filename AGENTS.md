# AGENTS.md

## What this is

`base-code-e2e` is a minimal, dependency-free Node HTTP server (`server.js`) used as a
fixture by Base44 Base Code end-to-end tests. Its rendered content is asserted by those
tests, so **do not change `server.js` copy, markup, or endpoints** unless explicitly asked.

## Running it here (Base44 sandbox)

Use the Base44 compose file, not the repo `Dockerfile` (that one `COPY`s the source into an
image, so edits would never show up):

```sh
docker compose -f docker-compose.base44.yml up -d --build   # bring up
docker compose -f docker-compose.base44.yml logs -f web     # logs
docker compose -f docker-compose.base44.yml down            # stop
```

- Single service `web`, node 20 on host port **3000**, source bind-mounted at `/app`.
- Start command is `node --watch server.js`, so edit `server.js` and the process restarts
  itself. There is no bundler or dependency install step (zero dependencies).
- Health: `GET /health` → `{"status":"ok"}`; the page is `GET /`.
- No database, no migrations, no environment variables, no external credentials.

## Gotchas

- `server.js` binds without an explicit host so it listens on both IPv4 and IPv6; leave that
  as-is, since the healthcheck probes `127.0.0.1`.
- `BASE44_PREVIEW_MODE` is forwarded into the container but the app does not read it; there
  are no sandbox-only code overrides in this repo.
