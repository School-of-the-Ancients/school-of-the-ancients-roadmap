# Module architecture and ownership

Updated September 24, 2026. This is the planning authority for module boundaries; it does not claim that code has already been extracted or accepted.

## Working model

Build composable modules in the existing repositories. A module has one responsibility, owned state, a versioned interface, explicit dependencies, and an acceptance fixture. A module is not automatically a separate repository, service, deployment, or commercial product. School and Matrix remain independently usable experiences assembled from these modules.

Matrix determines what actually happens in the world. AI Citizens chooses residents' intentions. School determines how to teach. Operator translates a human's construction requests. Connecting them does not combine their databases or authority.

## Module catalog

| ID / module | Owns | Required boundary / dependencies | Initial code home and acceptance |
| --- | --- | --- | --- |
| `world-runtime` — Matrix Core | Scene/entity identity, authoritative world state, finite action execution, physics, cancellation, receipts, scene persistence | Generic actions and observations; no curriculum, resident planning, or lifelog logic | Existing Matrix runtime; deterministic action/receipt/save/restore fixture, without School or Citizens |
| `operator` — Matrix Operator | Human voice/text construction intent, proposals, review/Apply UI, repair requests | Calls Core and Content contracts; does not own a second executor or resident mind | Existing Matrix service/UI; create → review → apply → undo with Citizens and School disabled |
| `content` — Content and capabilities | Asset catalogs, exact versions, validation, preparation, runtime registration | Core installation interface; asset availability never implies executable capability availability | Existing Matrix catalog/import code; bundled and cached-pack cold restore |
| `spatial-presence` — Spatial alignment and presence | Room/geospatial coordinate mappings, anchor/relocalization adapters, AR/VR views and navigation modes | Core world identity; capability-specific device adapters; imagery and room geometry are separate | Existing Matrix spatial code; alignment/recovery fixture and explicit device acceptance. Remote/astral presence is later work |
| `character-body` — Character embodiment | Avatar/rig bindings, animation, navigation and finite object interactions | Core executor; optional Content and Spatial adapters | Existing Matrix character code/issues; one commanded wave and one observed interaction without needs, memory or GOAP |
| `ai-citizens` — AI Citizens / Simulacra | Resident identity/card, beliefs and memories, needs, schedules, utility/GOAP policy, dialogue, relationships, simulation checkpoints | Bounded observations and action requests through a world adapter; Body only for embodied delivery | Initially a module in Matrix's existing repository; isolated fixture first, then two residents with contention, save/restore and replay; School absent |
| `school` — School learning | Historical mentor interpretation/source profile, teaching policy, lessons, assessment, learner records | Text/model adapter; optional world connector and presentation; Citizens is optional | Selected beta/v2/fresh School implementation after the existing audit; text lesson saves/resumes with Matrix, voice and Citizens absent |
| `human-interface` — Manfred | Personal lifelog ingestion, wearable input, consented context and human-state observations | Device/ingestion adapters; optional bounded world connector; private data remains separately owned | Existing Manfred codebase; capture → durable ingest fixture with School/Matrix absent; exact code paths to be audited before implementation |
| `integration` — Contracts and connectors | Capability negotiation, pairing, opaque ID correlation, compatibility, reconnect and error translation | Only the interfaces of enabled modules; no third authoritative world, resident or learner store | Adapters in existing processes; sample clients, missing-module/version mismatch fixtures and selected real end-to-end round trips |

School's historical source/teaching profile can reference a generic resident card when embodied; it does not duplicate or overwrite that resident's simulation memory. Learner knowledge and Manfred's personal history are separate records with separate access rules.

Demerzel/local compute supplies replaceable inference and job infrastructure. It is not a required module for the first lesson or resident fixture. Simulated NPC actions do not authorize real fleet jobs.

## Content and experience compositions

| Experience | Modules composed | Remains optional |
| --- | --- | --- |
| Matrix creative tool | Core + Operator + installed Content | School, Citizens, physical-camera capture |
| Standalone School | School + text/model and visual adapters | Matrix, Citizens, voice, headset |
| Embodied lesson | School + Integration + Core + exhibit Content | Body, Citizens, physical-room placement |
| Inhabited world | Core + Citizens + Body + world Content | School, Manfred; Spatial when room alignment is needed |
| Boulder digital world | Core + Spatial + geospatial/content packages | Citizens, School and Manfred integrations |

Boulder is a world-data/content workstream on these interfaces, not another engine. World's Fair is a School exhibit composition. Astral/remote presence belongs to Spatial Presence and must distinguish physical-body location from virtual-view/avatar location; it is not an NPC policy or a first-lesson gate.

## Interface and state rules

- Each module declares ID, interface version, required/optional capabilities, availability reasons, initialization/disposal, persisted schema/version, and a fixture command/evidence location.
- Core alone commits world changes and produces observed receipts. Operator, Citizens and School connectors submit supported intents; they cannot write transforms or claim execution directly.
- Preserve the existing review/Apply policy. Any scheduled resident automation needs an explicit bounded action policy; a model decision does not grant execution permission.
- Citizens' world adapter receives local permitted observations, legal candidate actions and world versions. It returns intention/action requests and reconciles accepted, failed, cancelled and unconfirmed receipts.
- One writer owns each state record. Connect stores with stable references; restore via versioned checkpoints and receipts rather than copying private databases.
- Optional modules can be disabled. Required capability absence blocks only the dependent feature with a useful reason. Core must not depend back on School, Operator policy, or Citizens policy.
- Generic STT/TTS, model providers, rendering, and character presentation remain replaceable adapters. Reuse interfaces before extracting shared packages; no synchronized deployment is assumed.
- Cross-module work specifies producer, consumer, version compatibility and independent acceptance on both sides. Current API examples remain proposals until validated.

## Existing issue ownership

Repository location is a code/tracking home, not the module boundary. Existing issue numbers, completed evidence and source references remain authoritative.

| Module / slice | Existing tracking |
| --- | --- |
| Core and foundation coordination | Matrix #12; executor/state #13A, optional programs #13B; acknowledged repair results #25; build/device evidence #24 |
| Operator | Matrix #12/#8 and proposal/repair portions of #25; discovery UI portion of #28 |
| Content | Matrix #9/#21/#28 |
| Spatial Presence | Matrix #22A/#26; #22B is the Body–Spatial integration slice |
| Character Body | Matrix #14/#15, sharing Core #13A; integration portion of #22B |
| AI Citizens | Matrix #29 coordinates #16–#20; Roadmap #14/#15 own community/policy evaluation; #29 links Body dependencies without owning Core execution |
| School | Roadmap #2/#6/#11/#13; teaching and lesson portions of #3/#5/#7/#8/#9 |
| Integration and presentation | Roadmap #4/#10/#12; input/presentation portions of #5/#7/#8; Matrix #31 contracts, #23 lesson acceptance, #32 reusable experiment actions |
| World/exhibit packages | Roadmap #3/#9; underlying generic Content remains reusable |
| Manfred, Boulder and later presence | Boundaries recorded here; link their existing owning backlogs before scheduling. No invented repository, issue or completed implementation |

References above use `Matrix` for [matrix-loading-operator issues](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues) and `Roadmap` for [this repository's issues](https://github.com/School-of-the-Ancients/school-of-the-ancients-roadmap/issues). 13A/13B and 22A/22B are sections of existing issues, not new issue numbers.

## Delivery and board rules

1. Record module ownership and the consumed interface in each scoped issue. For a shared issue, give each module a separate acceptance slice.
2. Inventory existing code and map it to these boundaries before moving files. Start with a small interface seam and fixture; preserve accepted behavior and saved data.
3. Pull independent slices: Core action fixture; Operator editing; School text lesson; Citizens policy fixture. Their independent gates do not wait for a full integrated showcase.
4. Connect one accepted pair at a time: intent → accepted action → observed receipt → consumer update. Run the module without its optional neighbors as well.
5. Extract a package, process, or repository only when independent build/release/reuse needs justify it. This plan does not require a rewrite or immediate repository split.

Keep one organization board with module-scoped views. Each issue body records **Primary module**, **Consumes**, and **Acceptance boundary**; these work immediately with the existing board. A future Module field/filtered views may mirror these IDs, but this document does not claim those board settings have been created. S0–S5 remain the School experience sequence; C0–C3 remain Citizens evaluation/integration gates. They are not one global waterfall. A documentation merge does not close runtime acceptance issues.
