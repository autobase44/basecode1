# Base44 dev environment notes

Minimal zero-dependency Node app (`server.js`, plain `node:http`). No package
manager, no database, no environment variables, no secrets.

## Running it here

```bash
docker compose -f docker-compose.base44.yml up -d --build
docker compose -f docker-compose.base44.yml ps
```

- `web` runs `node --watch server.js` from the bind-mounted repo, so edits to
  `server.js` take effect without a rebuild or restart.
- Preview entry point: host port 3000 (container port 3000, `PORT=3000`).
- Healthcheck probes the app's own `GET /health` endpoint.

## Verifying it works

```bash
curl -s http://localhost:3000/health   # -> {"status":"ok"}
curl -s http://localhost:3000/ | grep 'Base Code E2E'
```

The root page must contain the heading text `Base Code E2E` (marker:
`data-testid="e2e-marker"`).

## Don't change

This repo is a fixture for Base44 Base Code end-to-end tests; the page content
and the `/health` contract are depended on by those tests.
