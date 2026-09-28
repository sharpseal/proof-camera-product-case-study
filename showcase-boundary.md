# Public / Private Portfolio Boundary

## Public: useful for recruiters and technical interviewers

- Product problem and rationale
- Representative users and use cases
- High-level architecture and trust boundaries
- Product decisions and trade-offs
- Selected user journeys
- Representative Gherkin specifications
- High-level security and integrity principles
- Technology context at a non-sensitive level
- SDLC, review, acceptance, and evidence-governance method
- Sanitized UI screenshots or wireframes

## Private by design

- Kotlin / Java source code
- Gradle and release configuration
- Full backlog and ticket history
- Complete threat / abuse-case catalogue
- Exact algorithms, thresholds, security parameters, or key-management logic
- Storage schema and internal file layout
- Class/package architecture
- Complete automated/manual test suites
- Internal defect and remediation history
- Detailed runtime/release evidence
- Credentials, keys, tokens, signing material, or service configuration
- Raw AI working logs and prompt history

## Why this boundary exists

A portfolio reviewer should be able to answer:

> **Can this person frame a product problem, define system boundaries, write implementation-ready requirements, reason about risk, and govern delivery?**

They do not need the proprietary source code to answer that question.

The public case therefore demonstrates **reasoning, architecture, specification quality, and delivery discipline** while keeping the implementation private.

## Maintenance principle

This repository is intentionally **evergreen**. It documents durable product decisions and representative artifacts rather than mirroring every source commit, open issue, test run, or release status change in the private repository.

Material changes to the product strategy, architecture, trust model, or public portfolio narrative may justify an update. Ordinary implementation commits do not.
