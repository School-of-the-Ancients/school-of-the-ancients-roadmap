# School ↔ Matrix API proposal

Status: design proposal, September 22, 2026. Routes and message shapes below are not implemented endpoints. The contract issue will finalize them against the existing Matrix API and School implementation selected by the reuse audit.

## Independent products and authority

| Product | Owns | Does not own |
| --- | --- | --- |
| School of the Ancients | Mentor identity/teaching, learner conversation, curriculum, lessons, assessment, learning records | Unity internals, scene authority, asset installation internals |
| Matrix Loading Operator | Runtime capabilities, scene/content identity, proposals, user-approved commands, execution receipts, observations, scene checkpoints | Learner mastery, educational correctness, curriculum, School account database |
| Optional connector | Session pairing, capability translation, correlation, errors/reconciliation, presentation binding | A third canonical scene or learning store |

School must work without Matrix using its browser/text/voice/visual features. Matrix must work without School using its existing Operator. Another client should be able to use the same Matrix API. The connector can initially be an adapter in an existing PC process; independently versioned products do not require a new distributed microservice fleet.

## Connectivity

The current Matrix service is local to the PC; the public School website cannot simply call a user's `127.0.0.1` as a general integration solution. Validate browser mixed-content/private-network/origin behavior and authentication on actual supported clients before choosing transport.

The first integration decision compares a local companion/session pairing path with an outbound authenticated connector to School. Document origin allowlists, user-visible pairing, session ownership, credential storage, reconnect, and deployment model. Do not expose an unauthenticated local control port to the internet. A hosted relay or browser extension is not assumed required; select the smallest demonstrated route.

## Interface families

The names below are conceptual operations. Reuse existing transport/routes where possible; avoid duplicating the current planner, command queue, content registry, and receipt store.

| Operation | Result and policy |
| --- | --- |
| `discoverCapabilities` | Protocol/runtime versions; actions and schemas; availability/reasons; supported capture modes; exact installed content IDs |
| `pairSession` / `disconnectSession` | Explicit learner/facilitator-approved association between an opaque School session and one Matrix runtime lease |
| `readScene` | Bounded scene snapshot with authored revision, observations, room readiness, selected objects and provenance |
| `requestDemonstration` | Validated intent becomes a reviewable Matrix proposal; no direct scene mutation |
| `approveProposal` / `cancelRequest` | Reuse current Apply/Stop semantics; approval policy and actor are explicit |
| `readOutcome` / `readEvents` | Correlated accepted/running/failed/cancelled/unconfirmed outcomes and observed properties; reconnect cursor semantics |
| `requestCapture` | Explicit capture/preview/reference; capture does not automatically authorize sending to a model |
| `prepareContent` | Reuse catalog job stages; “ready” requires current runtime registration, not downloaded bytes |
| `saveScene` / `restoreScene` | Matrix owns scene snapshots; School owns learning checkpoints; connector coordinates receipts and recovery |

School receives generic selection/manipulation/action events and interprets them as learning evidence. Matrix need not understand quizzes or mastery. Mentor speech may run through a replaceable generic audio/presentation adapter while the text and learning record remain School-owned.

## Proposed envelopes

An illustrative request (actual capability IDs and schemas will be negotiated, not guessed):

```json
{
  "protocolVersion": "1",
  "requestId": "req-example",
  "integrationSessionId": "link-example",
  "runtimeSessionId": "runtime-example",
  "correlation": {"schoolSessionId": "opaque-session", "turnId": "turn-example"},
  "expected": {"authoredRevision": 42, "roomGeneration": 3},
  "intent": {"kind": "demonstration", "capabilityId": "advertised-capability", "parameters": {}},
  "approvalMode": "review"
}
```

An illustrative outcome:

```json
{
  "protocolVersion": "1",
  "eventId": "event-example",
  "requestId": "req-example",
  "runtimeSessionId": "runtime-example",
  "status": "succeeded",
  "commandReceiptIds": ["receipt-example"],
  "observed": {
    "authoredRevision": 43,
    "objectId": "block-example",
    "assetId": "known-unit-block",
    "coordinateFrame": "object-local",
    "units": "metres",
    "baselineDimensions": [0.1, 0.1, 0.1],
    "measuredDimensions": [0.2, 0.2, 0.2],
    "measurementMethod": "settled-mesh-bounds"
  },
  "captureRef": null
}
```

The final schema must distinguish acknowledgment, measured effect, partial result, and unknown outcome. The illustrative dimensions require an implemented measurement method and a known block; transform scale alone does not establish dimensions or volume. Derived values must declare their formula, baseline and geometry assumptions. An HTTP success means neither a completed scene edit nor educational success. Field limits, event ordering, durable replay retention, and version compatibility must be specified before implementation.

## Reliability, permissions, and privacy

- Stable request/event IDs and idempotency receipts prevent duplicate actions or checkpoint forks after retries.
- Unrelated simulation observations do not invalidate every proposal; relevant object/room/action dependency changes do. Reuse Matrix #13A instead of creating parallel revision rules.
- A timeout after dispatch is unconfirmed, not guaranteed failure. Query/reconcile before retrying. Reject stale callbacks as current-session mutations after disconnect, runtime replacement, or session load, while retaining/reconciling final receipts of already-dispatched work under its original request/runtime identity. Disconnection does not prove rollback.
- The initial flow retains explicit proposal review/Apply. Later finite authored automation needs a separate allowlist/policy; a conversational request does not unlock arbitrary execution.
- Send only the data needed for the current operation. Raw room imagery is transient by default and separately authorized for model inclusion. Record capture provenance, source versions, and observation IDs rather than indiscriminately retaining frames.
- Learner records and transcripts belong to School's existing access/export/delete policy. Matrix gets opaque correlation IDs, not unrestricted learner profiles or account tokens.
- Swapping School's learning implementation must preserve or migrate its records explicitly. Swapping a Matrix provider does not change lesson identity. Unsupported API versions return a useful compatibility error.

## Integration fixtures and acceptance

1. Matrix standalone works with School offline; School standalone works with Matrix absent.
2. A fake School client exercises Matrix contract fixtures; a fake Matrix adapter exercises School without Unity.
3. Actual School client → paired Matrix runtime → reviewed demonstration → receipt/measured result → mentor reply works on desktop, then headset.
4. Duplicate/out-of-order requests, dropped replies, revoked pairing, two competing clients, stale snapshots, and missing capabilities have deterministic recovery.
5. Save/restore reconciles both products without rolling back unrelated later learning records. Runtime restoration must be acknowledged before a matching learning checkpoint is resumed/forked.
6. The selected connection method works from the actual School browser/deployment and a clean local setup. A localhost demo alone does not prove hosted website connectivity.

An API reference, compatibility matrix, small sample client, and versioned recorded fixtures are deliverables of the contract work. No curriculum logic should be added to Matrix to satisfy this interface.
