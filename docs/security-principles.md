# Security & Integrity Principles

These are product-level principles, not a disclosure of the application's security implementation and not a certification claim.

## 1. Capture provenance is explicit

The system preserves a meaningful distinction between controlled in-app capture and media originating elsewhere. Provenance status should not be inferred merely from the existence of image bytes.

## 2. Local-first is a trust boundary

The core record lifecycle is designed around application-private local storage rather than requiring a remote service as the basic source of truth. This reduces unnecessary disclosure and keeps the core trust model understandable.

## 3. Integrity belongs to the record lifecycle

Integrity is not treated as a decorative hash displayed next to a photo. Media integrity information is part of a structured record lifecycle together with allowed context and state.

## 4. Platform security capabilities are used with bounded claims

Where Android platform security capabilities support local signing or integrity checks, the product treats those results as **local integrity evidence**. They are not represented as external timestamping, legal notarization, third-party certification, or proof of every real-world circumstance.

## 5. Export is an explicit security boundary

Moving proof material out of private local storage is a deliberate product operation with its own privacy and content rules.

## 6. External media does not silently become controlled capture

Gallery, imported, downloaded, or otherwise external media must remain distinguishable from media obtained through the controlled native capture path.

## 7. Security language is part of the product

Trust-related wording is governed with the same care as implementation. A claim should not become stronger than the requirement, system behavior, or available evidence supports.

## Threat-thinking examples

Representative questions used during design include:

- Can external media be mistaken for controlled capture?
- Can a user misunderstand contextual metadata as stronger proof than it is?
- Can ordinary navigation unintentionally disclose or export proof material?
- Can UI copy imply verification that the system did not actually perform?
- Can record state become ambiguous after lifecycle transitions?
- Can implementation status be reported more strongly than the available evidence allows?

## Claim boundary

Proof Camera is designed to create a **better-defined, more reviewable capture and record process**. It does not claim that a mobile application alone can establish every fact about a scene, operator, device, time, or event.
