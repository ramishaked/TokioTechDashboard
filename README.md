# Tokio Tech Dashboard

Generic demo of a municipal "Tech Matriculation Index" dashboard (Hebrew, RTL).
Demo city: Tokio. School data is fictional and lives in a published Google Sheet.
National series and the 33-municipality ranking are real (Israel Ministry of
Education, Excellence Report 2024); the Tokio row among them is fictional.

Live (same code, two hosts):
- https://tokio-tech-dashboard.vercel.app — Vercel, also serves `api/ask`
- https://ramishaked.github.io/TokioTechDashboard/ — GitHub Pages

## Layout
- `index.html`: the whole app, one file, no build step.
- `api/ask.js`: one serverless function behind the "ask the data" view.
  Deployed by the same Vercel project. Needs `ANTHROPIC_API_KEY`.
- `tools/`: local verification (`node tools/verify.mjs`). Not deployed.
- `data/national.json`: documentation copy of the reference constants; checked
  against `index.html` by `verify.mjs`.

## Data source
Google Sheet published to the web as CSV. One tab per sampling period
(`תשפו (1)` = start of year, `תשפו (2)` = end of year). Tabs are discovered
from the published HTML, with `GID_MAP` as fallback.
