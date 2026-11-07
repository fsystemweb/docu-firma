# AGENTS.md

DocuFirma is a frontend-only demo for managing digital document signatures. All data is simulated in React Context; there is no backend.

## Commands
- Install: `npm install` (lockfile: package-lock.json)
- Dev server: `npm run dev`
- Build: `npm run build` (runs `tsc -b` then `vite build`)
- Test: `npm test` (Jest, runs in band)
- Lint: `npm run lint`
- Deploy to GitHub Pages: `npm run deploy` (publishes `dist` with gh-pages)

## Conventions
- Stack: React 18, TypeScript 5, Vite 5, Tailwind CSS 4, shadcn-style Radix components, Jest 29 with Testing Library. ESM (`"type": "module"`), Node 22+.
- Structure: `src/pages/App.tsx` root, `src/components/` feature components, `src/components/ui/` shadcn primitives, `src/state/AppContext.tsx` app state, `src/lib/utils.ts` helpers, `src/types.ts` shared types.
- Tests live in `src/components/__tests__/`; `nanoid` is mapped to `tests/shims/nanoid.ts` in `jest.config.js`.
- Import from `src` with the `@/` alias.
- `vite.config.ts` sets `base` to `/docu-firma/` for GitHub Pages; keep it in sync with the repo name.
- Uploads accept PDF, DOC/DOCX and XLSX up to 10MB.

## Boundaries
- Always: add or update tests with every behavior change, and run `npm test` and `npm run lint` before finishing.
- Ask first: adding a dependency, changing the Vite `base` path, running `npm run deploy`.
- Never: commit secrets or read .env files.
- Never: add `fetch` or other network calls under `src/`; state stays in `src/state/AppContext.tsx`.
