# Working in this repo

Minimal Node fixture app (`server.js`, no dependencies). Deliberately kept simple:
its exact content is depended on by Base44 Base Code E2E tests — do not change
`server.js` copy, the `data-testid="e2e-marker"` heading, or the `/health` route.

## Running it here

Use the Base44 compose file, which runs the source with live reload:

    docker compose -f docker-compose.base44.yml up -d --build

- Single web service on host port 3000, bind-mounting the repo and running
  `node --watch server.js`.
- The repo's own `Dockerfile` is a production-style image (`COPY` bakes the source);
  it is intentionally **not** used for sandbox development.
- No dependencies, no database, no environment variables, no secrets.

## Verify

    curl -s localhost:3000/health          # {"status":"ok"}
    curl -s localhost:3000/ | grep e2e-marker

`node --watch` restarts on file changes, so edits appear without a rebuild.
