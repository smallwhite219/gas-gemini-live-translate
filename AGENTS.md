---
name: gas-gemini-live-translate
desc: Local governance for the GitHub Pages frontend of Gemini Live Translate practice.
---

# Local Rules

- This repo contains only the top-level browser frontend and public documentation.
- Do not commit Gemini API keys, Apps Script deployment secrets, access keys, token values, cookies, or local browser storage exports.
- The frontend may store the user's GAS Web App URL and optional access key in browser `localStorage` only after explicit user action.
- GAS remains the token backend. The long-lived Gemini API key belongs only in Apps Script Script Properties.

# Local Commands

- Static app: open `index.html` or serve the folder with any static web server.
- Basic validation: inspect browser console, microphone permission prompt, token request, WebSocket connection, and transcript output.

# State Entrypoints

- Task state: `docs/task-state.md`
- Phase log: `docs/phase-log.md`
- Release topology: `docs/release-topology.md`
