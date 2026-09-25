# Modular world, citizens and learning roadmap

**Start with the [short build plan and current School product brief](BUILD_PLAN.md).** It reconciles the September 25 implementation state and selects small next steps. The longer documents below retain the extended vision, source history and detailed acceptance; they are not a demand to rebuild already implemented features.

Current code homes: [Matrix Web + PC Agent Portal](https://github.com/School-of-the-Ancients/matrix-loading-operator) and the existing [text-first School implementation](https://github.com/School-of-the-Ancients/school-of-the-ancients). Matrix's [PRD](https://github.com/School-of-the-Ancients/matrix-loading-operator/blob/main/PRD.md) and [implementation plan](https://github.com/School-of-the-Ancients/matrix-loading-operator/blob/main/IMPLEMENTATION_PLAN.md) define its next creation/recovery slices. This repository remains planning and coordination, not another application.

**Composable modules with explicit interfaces and independent acceptance.**

This repository coordinates the module architecture and integrations for Matrix, AI Citizens, School of the Ancients and the human interface. Existing repositories remain code homes; modules do not require separate services or repositories.

| Module group | Responsibility |
| --- | --- |
| Matrix Core | Authoritative scenes, finite actions, observations and persistence |
| Matrix Operator | Human construction requests and reviewed scene editing |
| Content | Catalogs, asset preparation and runtime capability registration |
| Spatial Presence | Room/world alignment, AR/VR views and later remote presence |
| Character Body | Avatars, animation, navigation and finite interactions |
| AI Citizens / Simulacra | Memory, needs, schedules, planning and social behavior |
| School | Historical mentors, teaching, lessons and learner progress |
| Manfred / Human Interface | Wearable input, lifelogging and consented personal context |
| Integration | Versioned contracts, pairing, correlation and recovery |

**Matrix executes world actions; Citizens chooses intentions; School owns teaching.** Operator is a module of the Matrix experience. A School tutor does not require an autonomous resident, and a resident does not require School.

## Start here

- [Current build order, implementation snapshot and next-agent prompts](BUILD_PLAN.md)
- [Module catalog, ownership and dependency rules](MODULES.md)
- [Extended School experience PRD](PRD.md)
- [Extended module delivery plan and existing issue map](ROADMAP.md)
- [Module contracts and School–Matrix integration proposal](API-CONTRACT.md)
- [AI Citizens research](RESEARCH-AI-NPC-COMMUNITY.md) and [source index](RESOURCES.md)
- [Organization Kanban board](https://github.com/orgs/School-of-the-Ancients/projects/1)
- [Coordination issues](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues)

## Delivery

Start with bounded module slices and integrate accepted capabilities. School's first integrated experience remains predict → manipulate → observe → discuss → save/resume; S0–S5 describe that experience, not prerequisites for every module. Citizens research and standalone Matrix work can progress independently.

Boulder is a world-data/content workstream; World's Fair is an exhibit composition. Manfred connects the human to these experiences. Demerzel and local compute provide replaceable infrastructure.

## Implementation and evidence

Build on the existing Matrix implementation and current text-first School candidate. Preserve beta's useful mentor, conversation, visual and quest ideas; finish the concrete reuse/experience comparison before broader migration. Preserve the current v2 compatibility path until an explicit migration is accepted.

Keep one authoritative issue per capability, with module ownership and integration dependencies. Code remains in its owning repository; this is a planning repository. Use PRs for reviewable changes and recorded runtime/device evidence for completion. API shapes and module extraction are plans until implementation evidence exists.
