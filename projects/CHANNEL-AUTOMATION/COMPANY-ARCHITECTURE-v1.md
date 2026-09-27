# Channel Automation Company — Architecture v1

## Purpose
Build an automated content company for the channel around disability, inclusion, accessibility, mental/social wellbeing, assistive technology, communication, education, family and community topics.

The system is designed as a pipeline, not a one-off episode generator:

Research → Verification → Executive Decision → Story/Production → QA → Publishing → Analytics → Learning Loop.

## Leadership
### General Manager
Owns strategic direction, approves production priorities, and coordinates departments.

### Deputy Manager — Mahmoud
The continuity decision lead. Mahmoud monitors the manager's operational state and becomes Acting Manager when the manager is unavailable or fails a health check.

### Executive Watchdog
A constrained monitor. It checks manager heartbeat, decision freshness, workflow failures, and policy-gate status. It cannot silently rewrite production policy or publish arbitrary changes.

## Departments
1. R&D / Topic Intelligence
2. Research & Evidence Verification
3. Executive Decision / Editorial Board
4. Story & Script
5. Character & Visual Direction
6. Production Factory
7. QA / Accessibility / Rights / Safety
8. Publishing
9. Analytics & Learning
10. Maintenance / Self-Repair / Disaster Recovery

## Episode lifecycle
DISCOVER → RESEARCH → VERIFY → SCORE_FOR_FIT → APPROVE → SCRIPT → STORYBOARD → ASSETS → VOICE → ANIMATION/EDIT → QA → PUBLISH_READY → PUBLISH → MEASURE → LEARN.

No episode bypasses verification or QA.

## Topic diversity rule
The system must choose topics from a broad taxonomy and avoid near-duplicate episodes. A recurring character is allowed, but the central question, evidence, story problem, or educational value must materially differ.

## Character rule
The cartoon girl and her team are the channel's recurring fictional hosts. They present information through stories, situations, investigation and visual explanation. They are not presented as real people or as substitutes for qualified clinicians.

## Sensitive-topic rule
Medical, psychological, legal and rights-related claims require stronger source verification and conservative wording. The system must distinguish education from diagnosis, treatment, or individualized professional advice.

## Rights rule
Every production asset must have a provenance record: original, public domain, or compatible license. Unverified commercial assets and music are blocked.

## Continuity
The system keeps a last-known-good configuration and production state. If an agent or workflow fails, the system should isolate the failed component, preserve the last stable state, and escalate to Mahmoud.

## Self-repair safety
Self-repair is constrained to:
- diagnose;
- create a repair proposal;
- test in isolation;
- verify;
- deploy only after passing gates;
- rollback on failure.

An agent must not modify its own permissions or bypass approval gates.

## Emergency states
NORMAL → DEGRADED → MANAGER_FAILOVER → MAINTENANCE → ROLLBACK → RECOVERY → NORMAL.

The goal is service continuity, not autonomous control.
