# System Architecture

## Architectural objective

The system is designed around one central product requirement:

> **Preserve a clear, reviewable distinction between media acquired through the product's controlled capture path and media whose origin is outside that path.**

This is deliberately narrower than claiming that a mobile device can prove every fact about a scene. The architecture instead controls the parts of the lifecycle the application can reasonably own: acquisition path, record construction, local integrity semantics, storage boundary, export, and verification behavior.

## Context view

```mermaid
flowchart TB
    User[User / Field Operator]
    App[Proof Camera]
    Camera[Device Camera]
    Store[App-Private Local Storage]
    Recipient[Recipient / Verification Boundary]
    External[Gallery / External Media]

    User --> App
    App --> Camera
    App --> Store
    App -->|Explicit export| Recipient
    External -. outside trusted native-capture path .-> App
```

## Responsibility view

```mermaid
flowchart LR
    UI[Product UI & Guidance]
    Capture[Controlled Native Capture]
    Review[Review & Capture-Origin Gate]
    Record[Proof Record Construction]
    Integrity[Integrity & Context Binding]
    Vault[Private Local Vault]
    Export[Explicit Export]
    Verify[Verification Boundary]
    Context[Project / Case Context]

    UI --> Capture
    Capture --> Review
    Review --> Record
    Context -. contextual metadata .-> Record
    Record --> Integrity
    Integrity --> Vault
    Vault --> Export
    Export --> Verify
```

| Responsibility | Product purpose |
| --- | --- |
| Product UI & guidance | Explain the workflow, trust boundaries, actions, and consequences in user terms. |
| Controlled native capture | Acquire candidate media through the application's intended capture path. |
| Review & capture-origin gate | Keep external/untrusted origin distinguishable from controlled native capture. |
| Proof record construction | Turn an accepted capture into structured local record state rather than treating the image file as the whole product object. |
| Integrity & context binding | Associate integrity information and permitted contextual metadata with the proof record. |
| Project / case context | Organize work without confusing organizational metadata with proof of the underlying real-world event. |
| Private local vault | Keep the core record lifecycle local and under the application's private storage boundary. |
| Explicit export | Make disclosure/sharing a deliberate lifecycle step. |
| Verification boundary | Provide a place to evaluate exported record integrity and product claims without assuming external truth beyond the evidence carried by the record. |

## High-level data flow

```mermaid
sequenceDiagram
    actor U as User
    participant UI as App
    participant C as Capture
    participant G as Origin / Review Gate
    participant R as Proof Record
    participant V as Private Vault
    participant X as Export / Verification

    U->>UI: Start capture workflow
    UI->>C: Acquire candidate via in-app camera
    C->>UI: Candidate capture
    U->>UI: Review / accept
    UI->>G: Evaluate capture origin and product rules
    G->>R: Create structured proof record
    R->>V: Persist locally
    U->>UI: Choose export / verification action
    UI->>X: Prepare permitted record material
    X-->>U: Result / handoff
```

## Key architectural decisions

### 1. Local-first core
The product is designed so the basic proof lifecycle does not depend on a remote account or cloud service as its source of truth. This supports privacy, resilience, and clearer system boundaries.

### 2. Capture origin is a first-class state
Origin is not treated as incidental metadata. The product must preserve the distinction between controlled in-app capture and external media through the lifecycle.

### 3. Proof record ≠ image file
A proof record is a structured object combining the media with integrity information, lifecycle state, and permitted context.

### 4. Context is not evidence of truth
Project, case, or team labels can organize records, but they do not independently prove the event or scene represented by the media.

### 5. Export is a boundary
Moving proof material outside the application's private storage is treated as an explicit product action with its own rules rather than as a transparent implementation detail.

## Deliberately excluded implementation detail

This public architecture does not publish class/package structure, exact integrity algorithms, thresholds, key-management logic, local file layout, build configuration, dependency versions, full threat models, or internal test evidence.
