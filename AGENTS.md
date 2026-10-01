# Base Code E2E — Base44 Notes

Minimal zero-dependency Node.js web app (`server.js`), no database, no env vars, no external services.

## Run

```
docker compose -f docker-compose.base44.yml up -d
```

- Serves on port 3000; `GET /` shows the page, `GET /health` returns `{"status":"ok"}`.
- Uses `node --watch` (Node 20 built-in) for live reload on file changes — no extra dependencies needed.
- Source is bind-mounted; edits to `server.js` restart the server automatically.
