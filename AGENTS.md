# Base44 Setup Notes

Minimal Node.js HTTP fixture app (`base-code-e2e`). No dependencies, no environment variables, no database.

## Running in the sandbox

- `docker compose -f docker-compose.base44.yml up -d` brings up the app on port 3000.
- The source is bind-mounted into a `node:20-alpine` container; `node server.js` runs directly. There is no live-reload dev server (plain `http` module), so after editing `server.js` run `reload_preview` to see changes.
- Healthcheck: `GET /health` → `{"status":"ok"}`. The page at `/` shows the heading "Base Code E2E".
