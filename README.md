# files.wnbase.com

Two deployable pieces:

- **`index.html` + `404.html`** — the static frontend. Deploy both at the
  root of the repo (e.g. GitHub Pages). `404.html` is required for the
  path-based routes (`/username/shortid`) to work on GH Pages — see the
  comment inside it.
- **`server/`** — the Node/Express backend (file storage + username
  sharing + Clerk auth). This is a long-running process, not static —
  deploy it separately (a VM, Render, Railway, Fly.io, etc.) wherever you
  point `API_BASE`. See `server/README.md` for setup.

Config to check before deploying (top of the `<script>` in `index.html`):
- `API_BASE` — should point at wherever `server/` ends up running
- `ALLOWED_PLANNER_ORIGINS` — origins allowed to receive the postMessage
  when this app is opened from the planner's "+ Add File" flow
