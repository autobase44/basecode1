# base-code-e2e

Minimal Node HTTP fixture used by Base44 Base Code E2E tests.

## Do not change app content
`server.js`, `package.json`, and the page markup are asserted by the E2E tests.
Treat them as read-only.

## Run it in the sandbox
```
docker compose -f docker-compose.base44.yml up -d --build
```
- `web` runs `node --watch server.js` from a bind-mounted copy of the repo on a
  plain `node:22-alpine` image, so edits reload without a rebuild.
- Host port 3000 serves the app.

## Verify
```
curl -s http://localhost:3000/health   # -> {"status":"ok"}
curl -s http://localhost:3000/ | grep 'Base Code E2E'
```

No dependencies, no environment variables, no database, no external services.
