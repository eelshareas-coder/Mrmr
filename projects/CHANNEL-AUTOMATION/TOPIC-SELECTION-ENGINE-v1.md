# Topic Selection Engine v1

## Purpose
Select and prioritize genuinely different, useful, evidence-ready episode topics for the channel. This engine manages the full path from discovery to an executive decision; it does not auto-approve scripts or publishing.

## Inputs
Read:
- `TOPIC-QUEUE-v1.json`
- `TOPIC-DIVERSITY-GATE-v1.md`
- `TOPIC-SCOUT-STORY-STUDIO-CONTRACT-v1.md`
- `SOURCE-REGISTRY-v1.yml`
- the episode ledger of approved, in-production, and published episodes
- current production capacity and audience-learning notes, when available

Missing inputs must be marked UNKNOWN, never guessed.

## Pipeline
1. DISCOVER: collect candidates from research, official guidance, audience questions, lived-experience perspectives, and emerging technology.
2. NORMALIZE: assign a stable topic_id and fill the candidate card.
3. DEDUPLICATE: compare against all approved, active, and published episodes. Similarity is about the question/problem/takeaway, not title wording.
4. EVIDENCE TRIAGE: identify primary sources, evidence type, date, population/context, limitations, and unresolved claims.
5. SAFETY & RIGHTS TRIAGE: flag medical/psychological, legal, child-safety, privacy, stigma, and copyright risks; require qualified review where appropriate.
6. DIVERSITY GATE: apply the formal diversity contract. A candidate must differ in central question AND takeaway, plus at least two other dimensions. Any unresolved overlap = HOLD.
7. SCORE: calculate a transparent prioritization score only for candidates that pass hard gates.
8. STORY FIT: propose distinct story modes, character goal, and visual metaphor without changing the verified meaning.
9. EXECUTIVE REVIEW: present a ranked shortlist with evidence, uncertainty, trade-offs, and required human decision.
10. HANDOFF: only an explicitly approved candidate enters scripting. QA, accessibility, rights, and publishing authorization remain independent gates.

## Candidate card (required)
- topic_id; question; topic_identity; category; audience
- problem; intended takeaway; discovery_reason
- source_list; evidence_summary; evidence_strength; source_recency
- population_and_context; uncertainty; claims_needing_review
- sensitivity; rights_provenance; lived_experience_consultation_need
- story_mode; visual_metaphor; character_goal
- compared_episode_ids; diversity_result; hard_gate_status
- score_breakdown; recommendation; reviewer; decision_timestamp

## Hard gates (no scoring override)
Set BLOCK if a clear near-duplicate, unsupported harmful claim, rights violation, exploitative framing, or unsafe individualized advice is present.
Set HOLD if sources, population/context, rights provenance, diversity comparison, or required specialist review are missing.
Only candidates with all hard gates PASS may receive a priority score. A high score never overrides a HOLD/BLOCK.

## Priority score (0–100; transparent heuristic)
For gate-passing candidates, rate each dimension 0–5 and calculate weighted points:
- evidence readiness: 25%
- distinctness and topic diversity: 20%
- audience usefulness/relevance: 15%
- practical clarity and actionable learning (non-prescriptive): 10%
- story potential and visual explainability: 10%
- inclusion/accessibility value: 10%
- feasible production effort (higher feasibility = higher score): 5%
- freshness or meaningful new development: 5%

Formula: sum((rating / 5) * weight). Store every rating and a one-sentence rationale. If a dimension is UNKNOWN, do not silently score it as zero or five: mark score INCOMPLETE and send to research.

## Decision bands (only after gates PASS)
- 80–100: PRIORITY_SHORTLIST
- 65–79: RESEARCH_OR_DESIGN
- below 65: BACKLOG
These bands prioritize work; they are not truth, quality, or impact claims. Executive approval is still required.

## Diversity comparison
Compare at least:
1. central question;
2. intended takeaway;
3. primary problem;
4. evidence package;
5. character situation/goal;
6. story mode;
7. visual metaphor;
8. scene progression.
PASS requires a materially different question and takeaway, plus at least two additional dimensions. If evidence is insufficient, HOLD. Near-duplicate = BLOCK or REDESIGN before scoring.

## Output
Produce:
- ranked shortlist (only gate-passing topics);
- HOLD list with exact missing evidence/review;
- BLOCK/REDESIGN list with overlap or risk explanation;
- score breakdown and source ledger;
- recommended next action and accountable owner;
- audit record of inputs, rules version, timestamp, and human decision.
Never output only a winner: include meaningful alternatives and trade-offs.

## Operating rules
- Different episodes must have different central questions, not merely different titles.
- No fabricated sources, evidence, audience metrics, or completion states.
- Distinguish fact, interpretation, anecdote, uncertainty, and opinion.
- Do not infer an individual's needs from a diagnosis or category.
- Respect disabled people's agency; seek lived-experience input when the topic materially concerns their experience.
- Preserve accessibility, safety, rights, QA, audit, and publication gates.
- No automatic external posting, spending, permission changes, or irreversible action.
- If queue mutation is blocked, retain the scout report and state that the queue was not changed.

## Initial run against current seed queue
All eight TQ-001–TQ-008 are DISCOVERED candidates, not verified or approved. EXP-001 is the diversity baseline. The engine must not declare a winner until each shortlisted candidate has source triage, diversity comparison, and complete scoring. Existing scout leads for TQ-002, TQ-003, and TQ-004 are leads only; TQ-007 has a documented source gap. Preserve these states unless new evidence and a verified write update them.
