# Representative Business Analysis Specification

These examples show the specification standard used in the project without publishing the complete backlog or edge-case catalogue.

---

## Sample 1 — Trusted native capture origin

### Product risk

If media from outside the controlled capture path can silently acquire the same status as a controlled in-app capture, the product's provenance model becomes misleading.

### User story

**As a** reviewer relying on the proof-capture workflow  
**I want** the application to preserve the distinction between controlled native capture and external media  
**So that** the resulting record does not overstate how the media entered the workflow.

### Business rule

A media item that does not satisfy the controlled capture-origin boundary must not be represented as having the same capture provenance as an accepted native capture.

### Acceptance criteria

```gherkin
Feature: Trusted native capture origin

  Scenario: Controlled native capture proceeds toward proof-record creation
    Given the user started the in-app capture workflow
      And a candidate image was acquired through the controlled native capture path
    When the user accepts the candidate
      And the required product rules succeed
    Then the application may create a proof record
      And the capture-origin distinction remains part of the record semantics

  Scenario: External media is not promoted to trusted native proof
    Given media did not originate from the controlled in-app capture path
    When the application evaluates it for proof creation
    Then it must not receive the same trusted capture status as an accepted native capture
      And the distinction must remain visible in the resulting product state
```

### Non-functional considerations

- The rule must exist in system behavior, not only in explanatory UI text.
- Error or fallback states must not imply a stronger provenance result than was achieved.
- The wording shown to users must remain consistent with the underlying system state.

---

## Sample 2 — Explicit proof export

### Product risk

Locally held proof material may contain sensitive content. Moving it outside the private application boundary should therefore be deliberate and understandable.

### User story

**As a** record owner  
**I want** export to begin only after I deliberately choose an export action  
**So that** browsing or reviewing local records does not itself disclose or package them.

### Acceptance criteria

```gherkin
Feature: Explicit proof export

  Scenario: User requests export
    Given a local proof record is eligible for export
    When the user explicitly chooses an allowed export action
    Then the application prepares only the permitted export material
      And presents the resulting success, failure, or handoff state

  Scenario: Ordinary navigation does not initiate export
    Given the user is reviewing local proof records
    When the user opens, closes, or navigates between product screens
    Then no export is initiated solely because of that navigation
```

---

## Traceability model

```text
Problem / risk
    ↓
Business rule
    ↓
User story
    ↓
Acceptance criteria
    ↓
Implementation work item
    ↓
Engineering review
    ↓
PO / PM acceptance
    ↓
Evidence
    ↓
Release-safe claim
```

This model prevents a common failure mode in software delivery: treating the existence of code as proof that the original product requirement has been satisfied.
