# Primal Employee Monorepo

This repository aggregates multiple projects (including submodules). The primary web app lives in primal-user-view/.

- App (Next.js): primal-user-view/
- Third-party examples: third_party/
- Reference chatbot: vercel-ai-chatbot/

## Quick start (primary app)

cd primal-user-view
npm install
npm run dev

Open http://localhost:3000.

## Documentation
The full documentation is inside the app:

- primal-user-view/README.md — routes, architecture, Sphere of Influence, Development views, screenshots, env vars, and contributing.

## Submodules note
If you change files inside primal-user-view/, push there first, then commit the updated submodule pointer in this repository.
