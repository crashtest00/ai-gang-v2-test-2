# ai-gang-v2-test-2 — Project Map

<!-- Fill in each section before the first agent runs.
     Agents use this file to locate files efficiently — keep it concise.
     Update at the directory/pattern level when structure changes; not individual files. -->

## Framework / Runtime
Node 22 + Express (CommonJS). Started from AI Gang's `templates/web/`
deployment-target boilerplate — the same baseline `projects/hello-web/`
runs. Static hosting deployment target: server-side is a thin Express app
serving pre-built static assets plus a `/health` check; no SSR, no build
step required for the current boilerplate content.

## Key Directories
- `public/`      — static assets served directly by Express (`index.html`, `style.css`)
- `test/`        — `node --test` suite (`server.test.js`)
- `server.js`    — app factory (`createApp`) + entry point (`start`)

## Entry Points
- `server.js` — `npm start` / `npm run dev` runs it on `http://localhost:3000` (`PORT` env overrides)
- `public/index.html` — the page served at `/`
- `GET /health` — returns `{ "status": "ok" }`

## Conventions
- `createApp()` is exported separately from `start()` specifically so tests
  can mount the app on an ephemeral port without spawning a process —
  follow this pattern for any new routes/middleware rather than only
  wiring them inside `start()`.
- Plain CommonJS (`require`/`module.exports`), no bundler/transpiler in the
  boilerplate as shipped — introducing one is a real decision, not a given.
- Replace `public/index.html`, `server.js`, and `README.md` with the
  project's real content as work items land; this stub is a working
  baseline, not placeholder-only scaffolding.

## Test Framework
Node's built-in test runner (`node --test`, i.e. `npm test`) — see
`test/server.test.js` for the existing pattern (mounts `createApp()` and
asserts on responses).

## Available Agents
Single-repo project — one container subscribes to all agent channels
(`ai-gang-v2-test-2-dev`, no `AGENT_CHANNEL_SUFFIX` set):
- refinement (suffix: `refinement`)
- backend (suffix: `backend`)
- frontend (suffix: `frontend`)
- devops (suffix: `devops`)
