# Implementation roadmap and operating plan

Updated September 22, 2026. This is a plan; code, fixture results, live service state, and actual-device acceptance are separate evidence.

**Independent products:** School owns education and learner experience. Matrix owns the creative/spatial runtime. A versioned API connects them. Preserve beta's useful ideas while improving their implementation; the reuse audit and a standalone text-first slice choose a fresh or adapted School foundation before broad migration. Google live voice is not the application core.

[Product epic](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/1) · [Kanban](https://github.com/orgs/School-of-the-Ancients/projects/1) · [PRD](PRD.md) · [API proposal](API-CONTRACT.md)


## Ordered outcomes and implementation issues

| Phase | Outcome | New scoped work | Existing capabilities to reuse |
| --- | --- | --- | --- |
| S0 | Preserve beta; independent API | [Preserve beta: compare existing journeys and decide reusable School modules](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/2)<br>[Define and validate a client-neutral API for independent School and Matrix products](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/31) | [Matrix #8](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/8), [Matrix #21](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/21), [Matrix #24](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/24): scoped baseline/recovery work; no assumption of new live tests. |
| S1 | Standalone School and prepared lesson | [Text-first standalone School core](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/13)<br> [Define prepared exhibit packages and a simple readiness/launch flow](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/3)<br>[Connect School lesson sessions to Matrix requests, events and checkpoints](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/4)<br>[Add learner controls and explicit answer/question/scene-command voice routing](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/5) | [Matrix #23](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/23) authored baseline; [Matrix #21](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/21) only for lessons using external content; bundled content can proceed independently. |
| S2 | Historical mentor showcase | [Add a grounded historical mentor that teaches from observed Matrix outcomes](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/6)<br>[Present mentors with interruptible speech, captions and optional 3D avatars](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/7) | [Matrix #23](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/23) mentor acceptance; [Matrix #13](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/13) **13A** + [Matrix #14](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/14) only for optional embodied finite actions. |
| S3 | Interactive tools and creator flow | [Add a replaceable interactive lesson-panel adapter with feedback to the mentor](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/8)<br>[Add reusable parameterized experiment capabilities for interactive exhibits](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/32) | [Matrix #28](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/28) guided local publish/delivery, then catalog orchestration; [Matrix #9](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/9) category adapters. |
| S4 | World's Fair and facilitation | [Build a World's Fair exhibit library with VR visits and AR placement](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/9)<br>[Support a PC facilitator and headset learner with shared status and clear control](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/10) | [Matrix #22](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/22) **22A** for Quest 3 room acceptance; [Matrix #26](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/26) only for physical-image-dependent experiences. |
| S5 | Adaptive/shared expansion | [Connect adaptive curricula, learner knowledge and course materials to reusable exhibits](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/11)<br>[Evaluate multiheadset shared learning and choose a bounded networking design](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues/12) | [Matrix #29](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/29) optional generic NPC autonomy remains independently useful and outside the first teaching loop. |

Six repository milestones match S0–S5. They have no invented deadlines. Milestones organize product issues; capabilities in other repositories keep their own ownership. The epic spans phases and has no artificial due date.

## First work to pull

1. **School reuse audit**: compare beta/v2/Matrix with a real representative journey and decide which School modules to retain/adapt. Obtain user feedback on that demonstrated result.
2. **Matrix API contract audit and deterministic sample client**: can start alongside the reuse audit. Actual School-site pairing and full integration acceptance wait for the selected adapter/deployment path.
3. **Existing Matrix baseline acceptance**: #8 image/voice gaps, #21 scoped content/restart recovery, and #24 exact release/runbook work. These are Ready for scoped work, not already running or fully completed.
4. **Text-first standalone School slice**, with optional replaceable voice/visual adapters. Then **prepared lesson package + connector** and **headset answer controls**. Complete the authored scale lesson before requiring open-ended mentoring.
5. **Grounded mentor + presentation**; prove one unanticipated but supported question. Add richer tools based on observed lesson needs.

These are prioritized pulls, not a demand to complete the entire loader, every provider, or all release coursework before a bundled lesson can run. Physical-camera hardware, advanced NPCs, and Asset Store automation are separate tracks.

## Dependency rules

- School's standalone browser/text/voice experience and Matrix's standalone Operator must keep working if the connector or the other product is unavailable.
- S0's integrated exit requires the actual School deployment → paired local Matrix → reviewed action → observed receipt path. Local fixtures alone do not meet that gate.
- Contracts and fixtures can be built concurrently; dependent implementation waits only for the capability it consumes.
- Matrix **13A/13B** and **22A/22B** are sections of existing issues, not new issue numbers. Finite character actions need 13A; general behavior programs need 13B; final Quest 3 room placement needs 22A; room-aware NPC navigation needs 22B. An open parent issue does not imply all accepted subcapabilities are blocked.
- Use a portrait/caption/voice mentor before requiring rigs. Basic teaching dialogue does not depend on needs, GOAP, multi-NPC behavior or NPC memory.
- Capture is optional unless the lesson declares it required. Quest Pro virtual capture does not contain real-room pixels. Quest 3 mixed capture needs its own hardware evidence. Room anchors do not require camera imagery.
- External-pack lessons require exact dependency registration and restore; a bundled-prop lesson can proceed while broader catalog adapters remain unfinished.
- Interactive panels and experiment capabilities have independent contracts. Integrate one useful pair after each is accepted, rather than force an engine-wide rewrite.

## Reuse map across the organization

Existing issues retain implementation ownership. The board includes relevant reference work so the reuse audit can select it, not because every old backlog item is newly mandatory.

| Workstream | Existing authoritative or candidate issues | Decision |
| --- | --- | --- |
| Matrix foundations | [Matrix #12](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/12), [Matrix #8](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/8), [Matrix #9](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/9), [Matrix #21](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/21), [Matrix #22](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/22), [Matrix #24](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/24), [Matrix #25](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/25), [Matrix #26](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/26), [Matrix #28](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/28) | Continue existing implementations and acceptance; no duplicate loaders/capture/executors |
| Optional characters | [Matrix #29](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/29), [Matrix #13](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/13), [Matrix #14](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/14), [Matrix #15](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/15), [Matrix #16](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/16), [Matrix #17](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/17), [Matrix #18](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/18), [Matrix #19](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/19), [Matrix #20](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/20) | Independent general NPC track; consume only needed capabilities |
| Existing authored lesson | [Matrix #23](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/23) | Extend tested desktop integration into independent-product/headset acceptance |
| Beta conversation, visuals, voice | [beta #104](https://github.com/School-of-the-Ancients/sota-beta/issues/104), [beta #106](https://github.com/School-of-the-Ancients/sota-beta/issues/106), [beta #108](https://github.com/School-of-the-Ancients/sota-beta/issues/108), [beta #119](https://github.com/School-of-the-Ancients/sota-beta/issues/119), [beta #122](https://github.com/School-of-the-Ancients/sota-beta/issues/122), [beta #163](https://github.com/School-of-the-Ancients/sota-beta/issues/163) | Preserve product feel; validate/fix observed defects rather than assume current behavior |
| Beta curriculum, content, knowledge | [beta #112](https://github.com/School-of-the-Ancients/sota-beta/issues/112), [beta #113](https://github.com/School-of-the-Ancients/sota-beta/issues/113), [beta #114](https://github.com/School-of-the-Ancients/sota-beta/issues/114), [beta #118](https://github.com/School-of-the-Ancients/sota-beta/issues/118), [beta #120](https://github.com/School-of-the-Ancients/sota-beta/issues/120), [beta #253](https://github.com/School-of-the-Ancients/sota-beta/issues/253), [beta #254](https://github.com/School-of-the-Ancients/sota-beta/issues/254) | Candidate School implementation work; prioritize after reuse audit |
| v2 reusable contracts/voice/templates | [v2 #23](https://github.com/School-of-the-Ancients/sota-v2/issues/23), [v2 #29](https://github.com/School-of-the-Ancients/sota-v2/issues/29), [v2 #30](https://github.com/School-of-the-Ancients/sota-v2/issues/30), [v2 #31](https://github.com/School-of-the-Ancients/sota-v2/issues/31) | Optional reuse; existing Matrix API compatibility is evidence, not a mandated v2 migration |
| v2 artifacts/visuals | [v2 #27](https://github.com/School-of-the-Ancients/sota-v2/issues/27), [v2 #28](https://github.com/School-of-the-Ancients/sota-v2/issues/28), [v2 #65](https://github.com/School-of-the-Ancients/sota-v2/issues/65), [v2 #66](https://github.com/School-of-the-Ancients/sota-v2/issues/66), [v2 #67](https://github.com/School-of-the-Ancients/sota-v2/issues/67), [v2 #68](https://github.com/School-of-the-Ancients/sota-v2/issues/68), [v2 #69](https://github.com/School-of-the-Ancients/sota-v2/issues/69) | Compare with beta before implementing alternatives or a second artifact store |
| v2 adaptive curriculum | [v2 #76](https://github.com/School-of-the-Ancients/sota-v2/issues/76) | Existing design/reference for later School curriculum, not first-lesson prerequisite |

The [original beta rebuild requirement](https://github.com/School-of-the-Ancients/sota-beta/issues/252) already establishes a text-model learning core with STT/TTS adapters and explanation before Socratic questioning. [V2 #64](https://github.com/School-of-the-Ancients/sota-v2/issues/64) is an existing execution-plan reference, not a mandate to complete that remake.

Beta's Study Oracle and learner-knowledge ideas, richer generated visuals, creator templates, and optional character autonomy remain part of the full idea. The plan starts with a complete lesson because it tests whether those capabilities improve learning instead of accumulating disconnected features.

## Research references for agent experiences

These are design references for the School mentor and Matrix's optional character/simulation track, especially [Matrix #29](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/29). They do not add implementation gates to the first prepared lesson. Evaluate their ideas against learner value, observed behavior, and the independent-product boundary before adopting an architecture.

- **[TypeSafe AI documentation](https://docs.typesafe.ai/introduction)** — Typed Choice, Score, and truth-value questions over state, with confidence information. Reference for bounded agent decisions and routing; it is not a selected dependency.
- **[Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/pdf/2304.03442)** — Core vision reference for a living world of believable, interacting characters. Study its memory stream, reflection, retrieval, and planning mechanisms, then test which of them improve a historical mentor or exhibit.
- **[Simile](https://www.simile.com/) and its [research/blog](https://www.simile.com/blog)** — References for human-behavior simulation and validation. Related reading: [Social Simulacra](https://arxiv.org/abs/2208.04024), [Generative Agent Simulations of 1,000 People](https://arxiv.org/abs/2411.10109), [Finetuning LLMs for Human Behavior Prediction in Social Science Experiments](https://arxiv.org/abs/2509.05830), and [Building confidence in Simile](https://www.simile.com/blog/confidence). Use these to frame behavioral fidelity and evaluation, not to assume simulated people are accurate by appearance alone.
- **[MiroFish](https://github.com/666ghj/MiroFish)** — Open-source multi-agent simulation reference for turning seed material into an agent population, running interactions, and inspecting the resulting world and reports. Study its world setup, memory, and simulation workflow.
- **[ChatDev](https://github.com/OpenBMB/ChatDev) and [ChatDev: Communicative Agents for Software Development](https://arxiv.org/pdf/2307.07924)** — References for agent roles, structured communication, handoffs, and workflow orchestration. The paper describes the original virtual software company; the repository also contains the newer ChatDev 2.0 platform.

## Kanban policy

The organization Project has **Backlog → Ready → In progress → In review → Done**, plus **Blocked**.

- **Backlog:** recorded work; dependencies and approach may still need decisions. Imported old issues are not automatically active.
- **Ready:** a scoped next step has clear acceptance and can be pulled. A large parent issue must identify which slice is ready.
- **In progress:** work is actually underway; work-in-progress limit 3. Status is not inferred from old branches or historical linked PRs.
- **In review:** a reviewable PR/artifact and validation evidence are available.
- **Blocked:** record the concrete blocker, owner/next action and what can proceed independently. Lack of hardware blocks hardware acceptance, not all design/fixture work.
- **Done:** required acceptance is recorded. A merged PR, screenshot, completed animation, or model claim alone cannot establish complete learning/device acceptance.

Issue labels express area, priority and S0–S5 phase. Product milestones organize the new roadmap repository; existing v2 milestones are preserved. Dates stay unset until scope/dependencies and actual course requirements are confirmed. Use the Roadmap view for sequencing, not fabricated calendar commitments.

## Pull request and release policy

Keep runtime changes in their product repositories. Each PR names the contract/capability or issue slice it implements and verifies that the other product can be absent. Do not close umbrella issues while acceptance remains. Cross-product changes identify compatible versions and use contract fixtures before end-to-end checks.

Matrix #24 owns matched APK/service releases, checksums, version identity and coursework artifacts. Preserve previous releases unchanged. Lesson packages record exact content/mentor/source versions; a reproducible exhibit includes the selected School build/adapter, Matrix build, package and setup instructions. Course dates and reuse permission are historical constraints to verify, not promises in this roadmap.

## Evidence before a showcase

One actual learner completes predict → manipulate → observed result → mentor explanation → reflection → save/restart/resume. Include an unexpected supported question, model/voice failure fallback, connection loss and an unconfirmed command. A formative pilot with at least three unfamiliar users records setup assistance and learning/UX failures. Measure latency/frame time and independently score a transfer question; do not treat participation as mastery or a small pilot as efficacy proof.

No runtime implementation, live-service restart, device installation, or repository migration is performed by this planning work.
