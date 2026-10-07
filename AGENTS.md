# AGENTS.md

## Running in the Base44 sandbox
- `docker compose -f docker-compose.base44.yml up -d` starts the app; it listens on host port **3000**.
- The service runs `node --watch server.js` from the bind-mounted repo source, so edits to `server.js` restart the process without rebuilding.
- Healthcheck probe: `GET /health` (returns `{"status":"ok"}`). The page is `GET /`.
- No dependencies, no lockfile, no install step, no database, no environment variables or secrets.
- The repo has its own `Dockerfile`, but it copies the source into the image (production-style); the Base44 compose deliberately does not use it so edits stay visible.

## Notes
- `README.md` asks that the fixture's content stay unchanged (Base44 E2E tests depend on it).
