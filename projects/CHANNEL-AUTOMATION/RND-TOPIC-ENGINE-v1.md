# R&D Topic Intelligence Engine v1

## Mission
Continuously discover useful, evidence-based episode opportunities across disability, accessibility, inclusion, communication, education, family/social support, assistive technology, and mental/social wellbeing.

## Topic discovery
Candidate topics may come from:
- new research and reviews;
- official guidance and public institutions;
- recurring audience questions;
- misconceptions worth correcting;
- practical inclusion problems;
- emerging assistive technology;
- educational and social trends.

## Source hierarchy
Prefer, in order:
1. official guidance and public institutions;
2. systematic reviews/meta-analyses and peer-reviewed research;
3. reputable academic databases;
4. established professional organizations;
5. secondary sources only for discovery, not as sole evidence for sensitive claims.

## Candidate record
Each candidate must contain:
- topic_id
- question
- audience
- category
- discovery_reason
- source_list
- evidence_summary
- evidence_strength
- uncertainty
- sensitivity_level
- suggested_story_modes
- originality_notes
- duplicate_check
- rights_notes
- recommendation: HOLD / RESEARCH_MORE / SEND_TO_REVIEW

## Diversity engine
Before approval, compare the candidate with previous episodes using:
- central question;
- educational takeaway;
- story problem;
- evidence base;
- character situation;
- visual metaphor;
- format.

Near-duplicates are rejected or redesigned.

## Important boundary
The engine does not diagnose people or generate individualized medical/psychological treatment advice. Sensitive topics are educational and require appropriate review.


## Episode-to-episode diversity gate v1

Every new episode must introduce a materially different central topic/question from prior approved or published episodes.

### Required topic separation
A candidate is not considered distinct merely because its title, wording, example, or character dialogue changed. The candidate must differ in at least the central question and educational takeaway, and should also differ in story problem, evidence base, character situation, visual metaphor, or format.

### Hard duplicate blockers
BLOCK the candidate when:
- the central question is substantially the same as a recent episode;
- the same misconception/problem is being retold with only superficial wording changes;
- the same evidence package is reused without a genuinely new question;
- the proposed episode is effectively a scene-for-scene or claim-for-claim remake.

### Topic identity record
Each approved/published episode should record:
- topic_identity
- central_question
- educational_takeaway
- primary_problem
- evidence_package_id
- story_mode
- visual_metaphor
- character_goal

### Review behavior
If similarity is detected:
1. HOLD the candidate.
2. Identify the overlapping dimensions.
3. Either redesign the candidate around a new question/problem or reject it.
4. Do not advance it to APPROVED until the diversity gate passes.

### EXP-001 baseline
EXP-001 central question: "هل AAC يعني جهازًا؟"
Its topic identity is AAC definition/scope, not a general AAC efficacy episode, device review, or individualized AAC recommendation. Future AAC episodes must use a materially different central question and evidence package.
