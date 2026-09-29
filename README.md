# base-code-e2e

Minimal web app used as a fixture by the Base44 Base Code E2E tests. Please don't change it: the tests depend on its exact content.

- `npm start` (or `docker build -t base-code-e2e . && docker run -p 3000:3000 base-code-e2e`)
- `GET /` shows the page with the heading "Base Code E2E"
- `GET /health` returns `{"status":"ok"}`

No dependencies, no environment variables, no database.
