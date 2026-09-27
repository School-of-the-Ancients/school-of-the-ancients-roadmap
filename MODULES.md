# Cross-project ownership

Keep boundaries simple. Modules are responsibilities, not automatically separate services or repositories.

## Matrix

Canonical home: [matrix-loading-operator](https://github.com/School-of-the-Ancients/matrix-loading-operator)

Matrix owns:

- Three.js/WebXR world runtime;
- Operator;
- procedural generation and asset/Blender creation;
- interaction and physics;
- persistence;
- spatial VR/AR access;
- AI Citizens.

Within Matrix:

```text
Operator -> world changes -> Matrix runtime
                         -> persistence
                         -> humans / VR / AR
                         -> AI Citizens
```

Matrix executes world actions. Citizens choose resident intentions.

## School of the Ancients

Canonical home: [school-of-the-ancients](https://github.com/School-of-the-Ancients/school-of-the-ancients)

School owns:

- mentors;
- teaching policy;
- lessons/curriculum;
- learner input;
- assessment;
- learner records.

School may ask Matrix to create or manipulate an exhibit, but it does not own Matrix world state or Citizens memory.

## Manfred / human interface

Manfred owns private personal/wearable context and human-state input. It may provide bounded observations to other products with explicit consent, but its private history is not Matrix world state or a School learner record.

## Infrastructure

Model providers, local compute and agent workers are replaceable infrastructure. They should not become product architecture unless a concrete deployment need requires it.

## Integration rule

Connect products through narrow versioned actions/events rather than merging their state stores.

This repository documents those boundaries. Product implementation stays in the product repositories.
