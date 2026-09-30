# Base44 Dev Environment

Minimal Node.js HTTP server fixture (`server.js`) — no dependencies, no database, no environment variables.

## Running

```
docker compose -f docker-compose.base44.yml up -d --build
```

- App served on host port 3000.
- `GET /` → HTML page with heading "Base Code E2E".
- `GET /health` → `{"status":"ok"}`.
- Source is bind-mounted; `node --watch` restarts on edits to `server.js`.
- No secrets required.
