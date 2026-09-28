# Topic Diversity Gate v1

## Purpose
Prevent the channel from producing videos that are only cosmetic variations of one topic.

## Decision rule
Every episode must have a materially distinct:
- central question;
- educational takeaway.

It must also differ in at least two additional dimensions:
- primary problem;
- evidence package;
- character situation/goal;
- story mode;
- visual metaphor;
- scene progression/format.

## Duplicate rule
A candidate is BLOCKED if it substantially repeats a recent approved or published episode's central question or misconception, even when the title, wording, characters, or examples are changed.

## Required record
For each episode:
- topic_identity
- central_question
- educational_takeaway
- primary_problem
- evidence_package_id
- story_mode
- visual_metaphor
- character_goal
- diversity_check
- compared_episode_ids

## Outcomes
- PASS: materially distinct; may continue through the state machine.
- HOLD: insufficient information to establish distinction.
- REDESIGN: topic has potential but overlaps with an existing episode.
- BLOCK: near-duplicate or remake.

## EXP-001 baseline
- topic_identity: AAC-definition-scope
- central_question: هل AAC يعني جهازًا؟
- takeaway: AAC is a group of communication supports, not one device.
- story_mode: myth/fact
- visual_metaphor: one box opening into multiple communication modes
- diversity_check: baseline for future comparisons

## Invariant
The diversity gate may block or hold production, but it may never disable content QA, safety review, rights checks, accessibility checks, audit logging, or publishing authorization.
