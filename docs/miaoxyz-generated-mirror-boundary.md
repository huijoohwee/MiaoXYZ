---
doc_type: PRD-TAD-ADR-MVP-GTM
title: MiaoXYZ Generated Mirror Boundary
---

# MiaoXYZ Generated Mirror Boundary

## Objective

Make `huijoohwee/MiaoXYZ` the canonical development repository. Its Worker source, public storefront assets, migrations, and catalog are the authoring source. The production Pages tree at `huijoohwee/content/MiaoXYZ` is generated output owned by the protected Agentic Graph release workflow.

## Route ownership

- The Worker retains the D1-backed florist API and owns only `/MiaoXYZ/api` and `/MiaoXYZ/api/*` in production.
- The generated Pages mirror serves the storefront and static assets under `/MiaoXYZ`.
- `public/` remains the shared source input for local Worker development and generated Pages output.
- The protected release candidate records the exact MiaoXYZ source commit used to build both outputs.

## Guardrails

- Never edit `huijoohwee/content/MiaoXYZ` by hand.
- Never deploy the Worker, write production D1, or publish Pages from a developer checkout.
- A source merge does not deploy production. Candidate-bound production authorization remains separate.
- Preserve local `.dev.vars` and Wrangler D1 state; neither is committed.

## Acceptance

- `npm run dev` continues to run the local Worker from the MiaoXYZ repository root.
- The production Wrangler config declares only the two API route patterns.
- Repository documentation names the source and generated output owners consistently.
