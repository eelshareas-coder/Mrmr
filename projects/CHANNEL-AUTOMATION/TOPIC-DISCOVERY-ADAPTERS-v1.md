# Topic Discovery Adapters v1

## Purpose
Define the first discovery layer between R&D and the source registry. Adapters discover candidate topics; they do not approve claims or publish episodes.

## Adapter contract
Every adapter emits a normalized candidate with:
- topic_id
- question
- audience
- category
- discovery_reason
- discovered_at
- source_records
- suggested_story_modes
- sensitivity_level
- initial_uncertainty
- duplicate_check_status
- recommendation

## Adapter classes
### 1. Official guidance adapter
Input: configured official/public institution sources and publication/update feeds where available.
Output: new guidance, changed recommendations, recurring public questions, and accessibility developments.
Default evidence tier: tier_1.

### 2. Research adapter
Input: systematic review/meta-analysis feeds and peer-reviewed research indexes.
Output: new reviews, notable primary studies, evidence gaps, and research questions suitable for public education.
Default evidence tier: tier_2.

### 3. Professional/academic adapter
Input: professional organizations, academic institution publications, and reputable academic databases.
Output: educational explainers, emerging practice questions, terminology changes, and implementation problems.
Default evidence tier: tier_3.

### 4. Audience-question adapter
Input: first-party comments/questions when available and approved audience feedback exports.
Output: recurring misconceptions, practical inclusion questions, and requests for clarification.
Audience questions are discovery signals, not evidence.

### 5. Trend adapter
Input: reputable secondary sources and public trend signals.
Output: candidate subjects for further research.
Trend signals never become verified claims without independent evidence.

## Normalization rules
1. Assign a stable topic_id.
2. Preserve source provenance.
3. Deduplicate before editorial review.
4. Classify sensitivity before evidence collection.
5. Mark uncertainty explicitly.
6. Never upgrade discovery material to verified evidence automatically.
7. Send sensitive candidates to stronger verification.
8. Preserve the original discovery reason for auditability.

## Recommendation rules
- HOLD: insufficient novelty, relevance, or source quality.
- RESEARCH_MORE: potentially useful but evidence is incomplete.
- SEND_TO_REVIEW: sufficient discovery signal and a verification path exists.

## Failure behavior
If an adapter fails, record the adapter error and timestamp, keep the last successful registry snapshot, and continue only with unaffected adapters. A discovery adapter failure must never disable QA, safety, rights, or publishing gates.

## Next integration
The normalized output feeds TOPIC-DATABASE.json, then the Research & Verification Protocol. No topic becomes VERIFIED in this layer.