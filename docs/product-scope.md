# Product Scope & Decision Framework

## Product problem

Ordinary mobile photography is optimized for convenience. Images can arrive through the camera, gallery, screenshots, downloads, edits, messaging apps, cloud sync, or file imports. In many workflows that is exactly what users want.

A proof-oriented workflow has a different need: **the product must preserve meaningful distinctions about how a record entered the workflow and what the application can legitimately claim about it.**

Proof Camera is therefore designed around controlled capture, structured proof records, local integrity, bounded contextual metadata, private storage, and deliberate export/verification.

## Representative users

| User | Core need |
| --- | --- |
| Field operator / inspector | Capture visual material through a clear, repeatable product flow. |
| Record owner | Keep local proof records organized and understandable over time. |
| Reviewer / recipient | Understand what the record claims, how it was created within the product, and what it does not prove. |
| Technical / compliance stakeholder | Trace product rules to requirements, controls, acceptance logic, and delivery evidence. |

## Core capability areas

| Capability area | Product intent |
| --- | --- |
| First-use guidance | Explain the trust model, privacy boundary, and workflow before users rely on it. |
| Controlled native capture | Create a defined acquisition path for proof-oriented capture. |
| Review & origin handling | Preserve the distinction between controlled capture and media from outside that path. |
| Proof-record creation | Bind media to structured record state, integrity information, and permitted context. |
| Local organization | Group records by useful project/case context without overstating what those labels prove. |
| Private local vault | Keep the core lifecycle local and application-private by default. |
| Record review | Make record state and relevant provenance information understandable to the user. |
| Export | Move permitted proof material outside the private boundary only through an explicit action. |
| Verification | Evaluate the integrity semantics the product can support without converting them into broader real-world certainty. |

## Product principles

### Controlled, not magical
The product should make a process more controlled and reviewable. It should not market the device as an infallible witness.

### Local-first, not cloud-dependent
Remote services may be useful in future product directions, but the core product is designed so capture and local proof records have value without mandatory remote infrastructure.

### Bounded claims
Every user-facing trust statement should be explainable in terms of a product rule and evidence. Stronger wording requires stronger support.

### Explicit lifecycle transitions
Capture, acceptance, record creation, export, verification, and destructive actions are meaningful product transitions rather than incidental UI events.

### Organization is separate from proof
Project/case metadata helps users manage work. It is contextual information, not independent evidence that an event occurred as described.

## What this public scope intentionally does not include

The complete backlog, detailed abuse/threat catalogue, edge-case matrix, implementation-specific algorithms and thresholds, internal source map, complete test suites, defect history, and release evidence remain part of the private product workspace.
