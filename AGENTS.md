# AGENTS.md

Notes for Base44 sessions working in this repo.

## Running it here

This app is a single-process Node HTTP server with no dependencies, no database
and no environment variables (see `README.md`). Do not build the repo's own
`Dockerfile`: it `COPY`s the source into the image, so edits would not show up.

Use the Base44 compose instead — it bind-mounts the repo and runs
`node --watch server.js`, so an edit to `server.js` restarts the server:

```
docker compose -f docker-compose.base44.yml up -d
```

- Web entry point: host port 3000 (`/` shows the "Base Code E2E" page).
- Health: `GET /health` → `{"status":"ok"}` (also the compose healthcheck).
- Secrets: none. Nothing is read from `/run/base44/app.env`.

## Verifying

```
curl -s localhost:3000/health      # {"status":"ok"}
curl -s localhost:3000/ | grep e2e-marker
```

## Quirk

`README.md` asks that the fixture content stay exactly as it is — the Base Code
E2E tests depend on it. Keep changes to the app itself minimal.
