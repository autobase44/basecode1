# AGENTS.md

## Project

Minimal Node.js web app (`server.js`, no dependencies, no database) used as a Base44 Base Code E2E test fixture. Serves an HTML page on `/` and JSON on `/health`.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

- Node 20 Alpine base image, source bind-mounted at `/app`, live reload via `node --watch server.js`.
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Constraints

- **Do not modify `server.js` or `package.json`** — E2E tests depend on their exact content (see README).
- No external services, no secrets, no environment variables required.
