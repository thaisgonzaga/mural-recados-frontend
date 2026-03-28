# Project Guidelines

## Code Style
- Use Vue 3 with Composition API and `<script setup>`, following the pattern in `src/App.vue`.
- Keep the project in JavaScript (no TypeScript migration unless explicitly requested).
- Prefer the `@` alias for imports from `src` when it improves readability.
- Preserve current naming/domain language in Portuguese (`recados`, `autor`, `mensagem`) unless asked to rename.
- Keep component styles scoped when editing Vue SFCs (`<style scoped>`).

## Architecture
- This is a Vite + Vue 3 SPA frontend.
- App bootstrap is in `src/main.js` (Vue app + Pinia + Router registration).
- Current feature logic is centralized in `src/App.vue` and communicates with backend via `fetch`.
- Router exists in `src/router/index.js` but currently has no routes.
- Pinia exists in `src/stores/counter.js` as starter code and is currently unused by main feature flow.

## Build and Test
- Install dependencies: `npm install`
- Development server: `npm run dev`
- Production build: `npm run build`
- Preview build: `npm run preview`
- There is no automated test script configured in `package.json`; do not claim tests were run unless test tooling is added.

## Conventions
- Backend endpoints are currently hardcoded to `http://localhost:4000` in `src/App.vue`.
- For new API integrations, prefer introducing `import.meta.env` variables (e.g. `VITE_API_BASE_URL`) instead of adding more hardcoded URLs.
- When changing API calls, keep the same CRUD behavior used now: load list on mount, refresh list after create/delete.
- Keep changes focused and minimal. Avoid introducing router/store refactors unless requested.

## Documentation
- For setup and base scripts, see `README.md`.
- For README generation standards in this workspace, see `.github/prompts/readme-completo.prompt.md`.