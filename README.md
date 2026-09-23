# School of the Ancients — product and integration roadmap

**Two independent products, connected through an API.**

- **[School of the Ancients](https://schooloftheancients.com/)** owns the academy, historical mentors, conversation, lessons, assessment, and learner progress. Preserve the useful ideas and compelling interactions of the older [sota-beta](https://github.com/School-of-the-Ancients/sota-beta). A fresh text-first School implementation is an option, with selective reuse from beta or [v2](https://github.com/School-of-the-Ancients/sota-v2) where it helps.
- **[Matrix Loading Operator](https://github.com/School-of-the-Ancients/matrix-loading-operator)** owns loading and editing scenes, content, spatial interactions, and observed runtime results. It remains useful as a standalone creative tool and can support other clients.
- **The optional integration** lets a mentor request supported demonstrations and receive observed results. Neither product embeds the other product's domain or directly edits its database.

This is a **planning and API-design repository**, not a new app implementation. Application code stays in the existing repositories. New implementation work belongs with its owning product; this repository tracks product outcomes, unresolved ownership decisions, and integration acceptance.

## Start here

- [Product brief / PRD](PRD.md)
- [Ordered delivery plan and issue map](ROADMAP.md)
- [Agent experience research references](ROADMAP.md#research-references-for-agent-experiences)
- [Proposed cross-product API contract](API-CONTRACT.md)
- [Organization Kanban board](https://github.com/orgs/School-of-the-Ancients/projects/1)
- [Product and integration issues](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues)

The first experience is one complete prepared lesson with an AI historical mentor: predict → manipulate → observe → discuss → save/resume. Later, those exhibits form a World's Fair that can be visited in VR or brought into a real room in AR.

## What is decided

1. Build on the current Matrix Operator.
2. Preserve beta's good mentor, conversation, visual, and quest ideas while improving their implementation.
3. Connect independent products through versioned capabilities, requests, events, and receipts.
4. Begin with prepared content and supported actions; add capabilities when lessons justify them.
5. Keep all roadmap items planned until their acceptance evidence exists.

## What is not decided

The first reuse audit and a bounded standalone slice choose where School's future learning modules live and whether to build fresh or adapt tested code. Beta's Google live-voice architecture is not the target: a provider-neutral text/lesson core owns state, with optional STT/TTS and visual adapters. Matrix currently has an adapter to v2's durable lesson API; this is a compatibility path to preserve, not a commitment to make v2 the new product. API examples in this repository are **proposals, not currently deployed endpoints**.

## Working agreement

Use issues for outcomes and acceptance, the board for current work, and PRs for reviewable changes. Keep one authoritative issue for each existing capability. Link related beta/v2/Matrix work rather than duplicating it. Product/lesson issues do not turn the reusable Matrix runtime into an education-specific application.
