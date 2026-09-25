# Build plan: finish useful slices, then expand

September 25, 2026. This is the short, current execution guide. [MODULES.md](MODULES.md) retains ownership definitions; [PRD.md](PRD.md), [ROADMAP.md](ROADMAP.md), and existing issues retain the extended vision and detailed acceptance. No code migration, issue closure, or board change is implied.

## Where work belongs

| Repository | Work |
| --- | --- |
| [matrix-loading-operator](https://github.com/School-of-the-Ancients/matrix-loading-operator) | Current Web Matrix, PC Codex portal, reusable world/asset tools; preserve Unity as the native/legacy track. Start with its [PRD](https://github.com/School-of-the-Ancients/matrix-loading-operator/blob/main/PRD.md) and [implementation steps](https://github.com/School-of-the-Ancients/matrix-loading-operator/blob/main/IMPLEMENTATION_PLAN.md). |
| [school-of-the-ancients](https://github.com/School-of-the-Ancients/school-of-the-ancients) | Existing text-first School implementation and limited Matrix connector. Continue this candidate; no third School rewrite. |
| This roadmap repository | Product decisions, cross-repository order and research. Do not add runtime code here. |
| `sota-beta` / `sota-v2` | Experience/code references and existing compatibility paths. Do not delete, migrate records, or resume every old backlog item automatically. |

Modules are ordinary code boundaries unless a real deployment need says otherwise. Do not turn the nine ownership labels into nine new services or packages.

## Current evidence, not another starting-from-zero plan

Inspected Matrix main: `509a72a344faa8e2cc63c12b67a6b08d140c43ce` (PR #80). Roadmap main: `4094e40c50eae8818fd3c6297876786dca38c162` (PR #17). School main: `d2a966b48ff64d6eb9b4ae3f0a63a87e9d05c955`.

School main already contains the standalone Galileo/scale lesson, durable local records, a replaceable Codex text provider, reviewed Matrix block placement/scaling and optional local read-aloud. See the [current implementation README](https://github.com/School-of-the-Ancients/school-of-the-ancients/blob/main/README.md) and PRs #1–#4.

At review time, [School PR #5](https://github.com/School-of-the-Ancients/school-of-the-ancients/pull/5) is **open/draft**: mentor-directed scene demonstrations. [PR #6](https://github.com/School-of-the-Ancients/school-of-the-ancients/pull/6) is **open**: optional dictation, visual adapters and audit 2A. Both target `main`; they are not a required stacked chain. Review their overlap and combined tests before any authorized merge. Legacy beta PR #257 is separate, not the default implementation path.

Matrix already has the Web runtime, portal, GLB catalog, animations, numeric components and browser persistence. Newer Quest acceptance and a complete rich Blender MCP conversation remain gaps. A merged PR or local test does not prove deployment or headset behavior. This planning pass did not rerun runtime tests.

## School product brief for the next release

**Goal:** one useful historical-mentor lesson that works in an ordinary browser and can optionally use the current Matrix Web runtime.

The learner chooses Galileo, gets an explanation/example, makes a prediction, changes a block's dimensions, discusses the observed result, asks a related follow-up, and saves/resumes. Text is sufficient. The character is a disclosed AI interpretation, not a source of invented historical quotations.

School owns teaching, learner input, transcript and learning records. Matrix owns world execution and observed effects. A reusable experiment has one owner for its state/calculation; HTML/Three.js/XR are presentations, not divergent simulations. Keep lesson records distinct from experiment state and NPC memory.

**Release acceptance:** complete the lesson with Matrix and voice disabled; repeat its optional demonstration using the real Web Matrix and matched receipts; handle “only width doubles”; resume the correct lesson/experiment after restart; fail honestly when a provider or runtime is unavailable. An animation, successful command, or completed lesson does not establish physical measurement or learner mastery.

**Not required:** a moving avatar, autonomous citizens, Boulder, realtime voice, paid asset APIs, hosted access, multiplayer, a complete World's Fair, or migration of beta/v2 records.

## Work in these small steps

| Step | Reuse / smallest change | Exit | Existing owner |
| --- | --- | --- | --- |
| **S0 — Review the existing School candidate** | Review open PRs #5/#6 rather than recreating them. Exercise main's text-only lesson and save/resume. Finish the concrete beta-experience comparison; keep unresolved gaps visible. | A reviewed working candidate and a recorded keep/change decision. Each PR is independently reviewed; merge only when authorized. | Roadmap #2/#13; School PRs #5/#6 |
| **S1 — Share one browser experiment** | Use the existing scale lesson and Matrix M3. Select one calculation/state implementation; connect HTML controls, Three.js view and normalized operation/results. Start with built-in blocks. | Equivalent input produces equivalent state/results; changing surfaces does not fork the lesson or experiment. No new general plugin framework. | Roadmap #3/#8; Matrix #31/#32 |
| **S2 — Complete the optional WebXR lesson loop** | Extend the existing limited local companion, not the privileged Codex portal. Request → review/Apply → runtime receipt → mentor explanation. Use supported WebXR placement; keep text/portrait fallback. | One real browser/Quest lesson, a related surprise question, interruption and coordinated save/resume. Restore world state before claiming the linked demonstration is current. | Roadmap #4/#5/#6/#7; Matrix #23 |
| **S3 — Make it easy to use again** | Fix observed launch/readiness/input issues; optionally add a second prepared lesson and one-PC/one-headset facilitator controls. | Another person can start and resume without editing provider JSON. Record limitations and freeze a reproducible version. | Roadmap #3/#9/#10; Matrix #24 |

S0 can proceed alongside Matrix M0–M2. S1 uses the capabilities it needs from Matrix M3; it does not wait for a fancy Blender model. S2 waits for the relevant WebXR/runtime evidence, not every Matrix umbrella issue. These steps select small slices from the older S0–S5 roadmap; they do not redefine or automatically close those broader milestones.

## Later work stays visible, not mandatory

| Lane | Existing issues | Trigger |
| --- | --- | --- |
| More content/providers | Matrix #9/#28 | The next actual experience needs an unavailable asset/type. Add one provider. |
| Character body and Citizens | Matrix #13–#20/#29 | Choose one finite interaction, then a tiny routine; School does not wait for it. |
| Boulder and remote presence | Matrix #38/#41 | A concrete world/registration experiment; use existing prototype evidence. |
| Adaptive teaching | Roadmap #11 | The first lessons and records work; no automatic full-course generator. |
| Shared multiheadset world | Roadmap #12 | A demonstrated need beyond one facilitator/headset. |
| Community/fast-model research | Roadmap #14/#15/#18 | Reproducible comparison to a simple authored/utility baseline before adoption. |
| Live agents, wearables and infrastructure | Matrix #62; existing Manfred/Demerzel work | A specific unmet input/provider need. Reuse existing adapters; no fleet dependency for one lesson. |

Keep the [research resource index](RESOURCES.md), [research review](RESEARCH-AI-NPC-COMMUNITY.md), and Matrix's resource-input table. A new link is a candidate, not an instruction to replace the active stack.

## GitHub and agent rules

Keep existing issues as owners. The Markdown tables provide the work order without requiring new board fields, labels, milestones or duplicate epics. Update one step's status/evidence when it changes. Only extract a new issue when an actual uncovered task appears.

Prefer one active Matrix PR and one independent School PR over long speculative stacks. Each PR names its outcome, existing code reused, excluded scope, tests actually run, and outstanding wearer checks. Run School tests/typecheck plus the documented cross-repository fixtures for connector changes; confirm what was skipped. Do not automatically merge, close umbrella issues, change public access, or move code.

**Next School prompt:** “Read this BUILD_PLAN.md and the School implementation README/AGENTS instructions if present. Check current main and open PRs #5/#6. Work on S0 only: review/reconcile existing work and demonstrate the standalone lesson before proposing new code. Keep Matrix optional. Report actual evidence and remaining gaps; do not migrate beta/v2 or merge automatically.”

## Review scope

This plan reconciles available recent conversation summaries, both issue inventories, recent PR descriptions/evidence, project maps, implementation READMEs, ownership documents and resource indexes. It is not a claim that every chat transcript, every code diff, every external resource, or all hardware was reviewed. Recheck current refs and actual PR state before execution; this snapshot will age.
