# Clearpath – Blockchain-based NGO Donation Tracker

Clearpath is a transparent charity-funding platform. Donors give to an NGO project, and the money stays locked in escrow until independent verifiers approve proof of completed work. Every donation, vote and release is recorded in a public ledger.

> **Note:** This is a demonstration prototype. Blockchain transactions are simulated. No real money, wallets or keys are involved.

## Features

- **Role-based workspace:** Donor, NGO and Verifier views, switchable from the top bar.
- **Milestone-based escrow:** each project is split into milestones. A milestone's funds are released only after 2 of 3 verifiers approve its evidence. A rejection keeps the funds locked and records a reason.
- **Photo proof of work:** NGOs attach site photos to each milestone. Donors and verifiers see them in a clickable gallery.
- **NGO ratings and reviews:** donors who have contributed to an NGO's project can rate it from 1 to 5 stars and leave a review. Each donor gets one rating per NGO, and rating again updates it.
- **Public ledger:** a filterable timeline of donations, evidence submissions, votes and releases, each with a simulated transaction hash.
- **Project management:** NGOs can create projects, edit milestones and submit evidence.
- **Contribution history:** every donation is listed with its donor, amount and reference.

## How it works

1. An **NGO** creates a project and divides it into milestones.
2. **Donors** contribute to the project pool. Funds are held in escrow.
3. The NGO completes a milestone and submits **evidence**: a description, location, files and photos.
4. **Verifiers** review the evidence and vote. Two approvals release exactly that milestone's amount. Two rejections send it back to the NGO for revision.
5. Every step is written to the **public ledger**, and donors can **rate** the NGO afterwards.

## Tech stack

- React 19, TypeScript, Vite
- Tailwind CSS, shadcn/ui, Lucide icons
- wouter (routing), TanStack Query
- pnpm workspaces (monorepo)
- Express 5, PostgreSQL and Drizzle ORM scaffolding (not used by the demo)

## Project structure

```
artifacts/
  ngo-donation-tracker/   Main web app (donor, NGO and verifier views)
  api-server/             Express API scaffold (health check only)
lib/
  db/                     Drizzle ORM schema (empty scaffold)
  api-spec/               OpenAPI spec and code generation
```

The app's logic lives in `artifacts/ngo-donation-tracker/src/App.tsx` and `src/lib/demo-state.tsx`. Sample proof photos are in `public/proof/`.

## Getting started

**Requirements:** Node.js 20 or newer and pnpm (`npm install -g pnpm`).

```bash
pnpm install
pnpm --filter @workspace/ngo-donation-tracker run dev
```

Then open **http://localhost:5173**.

The demo needs no database or backend. Its data is saved in your browser's localStorage. Use **Reset demo data** in the sidebar to restore the sample project.

## Demo walkthrough

1. As a **Donor**, open "School Construction" and make a contribution.
2. Scroll down to rate the NGO. Use the name "Mira Patel", who has donated but has not rated yet.
3. As an **NGO**, open "Submit milestone proof", choose a milestone and click **+ Add sample photos**.
4. As a **Verifier**, open "Verify milestones", review the photos and approve with two different reviewers.
5. Check the **Public ledger** to see every action recorded.

## Limitations and future work

- The blockchain is simulated. There is no smart contract, wallet connection or live network.
- Data lives only in the browser, with no backend persistence.
- There is no real authentication. Roles are chosen from a dropdown.
- Planned: a Solidity escrow contract, MetaMask integration, IPFS storage for evidence and a real backend with login.
