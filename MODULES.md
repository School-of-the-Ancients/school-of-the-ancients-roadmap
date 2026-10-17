# Cross-project ownership

Three independent products share capabilities. Modules describe responsibility and state ownership; they do not automatically require separate services or repositories.

## Matrix Loading Operator

Home: [matrix-loading-operator](https://github.com/School-of-the-Ancients/matrix-loading-operator).

Matrix is the shared tool for creating, presenting and interacting with digital worlds. It owns:

- Three.js/WebXR world execution, entity identity, interaction and physics;
- Operator and the existing procedural, asset and Blender creation paths;
- content registration, compatible world saves and execution receipts;
- desktop/VR rendering, generic room AR, local alignment and supported placement.

School and Civilization ask Matrix for supported actions and inspect their results. Matrix remains usable for open-ended creation without either experience.

## School of the Ancients

Home: [school-of-the-ancients](https://github.com/School-of-the-Ancients/school-of-the-ancients).

School is the Cosmos-style fair of historical minds: choose a subject, meet an appropriate guide, converse and explore. The guide can ask Matrix to load or manipulate presentation material as supported capabilities become available.

School owns mentor identity and sources, conversation, teaching policy, lessons, assessment and learner records. Matrix supplies the avatar/presentation and world tools when connected. A guide can use a generic Matrix entity without resident needs, schedules, social memory or a running Citizens simulation.

The existing Galileo lesson is a small integration reference. It does not define all of School or establish that the broader exploratory VR experience is already implemented. School remains independently usable without Matrix.

## Civilization

Current implementation location: Citizens code in [Matrix](https://github.com/School-of-the-Ancients/matrix-loading-operator). Existing owner: [Civilization / Citizens #29](https://github.com/School-of-the-Ancients/matrix-loading-operator/issues/29).

Civilization owns AI residents and society, their memory/planning/social behavior, geographic world data, Boulder reconstruction and the AR overlay associating the digital city with real locations. It uses Matrix for rendering, entities, physics, assets, interactions and world actions.

Generic headset access and local room tracking stay in Matrix. Geographic coordinates, city meaning and the mapping of residents/places into that overlay belong to Civilization. Private human location is an explicitly permitted external observation, not simulation truth.

This is a logical module boundary. Existing code and issues remain in Matrix; a separate package, repository or service has not been created by this record. Clarify the world adapter and lifecycle before extraction. School can later visit an inhabited exhibit, but Civilization is not a required successor to a School lesson.

## Manfred and infrastructure

Manfred owns private personal/wearable context. It may provide bounded, consented observations to selected consumers; private human history is not a world save, resident memory store or learner record.

Model providers, compute, agent workers and content providers are replaceable infrastructure. They do not need independent product roadmaps merely because they are separate tools.

## Integration rule

Use narrow versioned capabilities, requests, observations and receipts. School owns mentor/learning sessions; Civilization owns resident/simulation state; Matrix owns world execution and supported scene state. The same character can be presented in Matrix without merging those identities or databases.

Each world has one authority for world changes. A connected Civilization simulation has one simulation owner, not a new clock per visitor. Consumers choose intentions; Matrix validates and executes. Current permissions apply, and a teaching role does not grant PC credentials or unrestricted world control.

Product repositories and their existing trackers own implementation. [ROADMAP.md](ROADMAP.md) links those queues; this catalog defines the boundary.
