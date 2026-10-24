# Changes in this version

Two features were added. The existing UI, pages, colours and logic are unchanged.

## 1. NGO rating (donor reviews)
- Project page: new "What donors say about <NGO>" section with average, 1-5 star breakdown, reviews and a "Rate this NGO" form.
- Only donors who have contributed to that NGO's project can rate. One rating per donor per NGO (rating again updates it).
- Project cards on the home page show the NGO's average rating next to "Led by ...".
- NGO workspace shows the same ratings (read-only) at the bottom.
- Demo data: two seeded reviews. "Mira Patel" has not rated yet, so you can try it straight away.

## 2. Proof of work photos
- Milestone cards (project page) and the verifier review cards show a "Photo proof" gallery; click a photo to enlarge (arrow keys / Esc work).
- NGO workspace > Submit milestone proof: upload photos (images are resized and previewed) or click "+ Add sample photos".
- Six sample photos are in `artifacts/ngo-donation-tracker/public/proof/`. Replace them with real photos if you like.
- Verifiers see a note when no photo was attached.

## Files changed / added
- `artifacts/ngo-donation-tracker/src/App.tsx` (new components + small hooks into existing pages)
- `artifacts/ngo-donation-tracker/src/lib/demo-state.tsx` (ratings, photos, `rateNgo`, migration of old saved demo data)
- `artifacts/ngo-donation-tracker/src/index.css` (styles appended at the end)
- `artifacts/ngo-donation-tracker/public/proof/*.svg` (new sample photos)
- `replit.md` (notes), `CHANGES.md` (this file)

## Windows fixes (added later)
- `package.json`: the `preinstall` script used `sh`, which Windows does not have. It now uses Node (still blocks npm/yarn).
- `pnpm-workspace.yaml`: removed the overrides that excluded the Windows (`win32-x64`) builds of esbuild, rollup, lightningcss and tailwind-oxide, so the dev server works on Windows.
- `vite.config.ts`: PORT defaults to 5173 and BASE_PATH to `/` when not set (Replit still sets its own).
- Run: `pnpm install`, then `pnpm --filter @workspace/ngo-donation-tracker run dev`.
