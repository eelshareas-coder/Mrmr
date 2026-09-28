# Automation State Machine v1

## Company states

| State | Meaning | Owner |
|---|---|---|
| NORMAL | All critical services healthy | General Manager |
| DEGRADED | Non-critical service failure | General Manager / Mahmoud |
| MANAGER_FAILOVER | Manager unavailable | Mahmoud |
| MAINTENANCE | Repair in progress | Maintenance Team |
| ROLLBACK | Last-known-good restoration | Maintenance + Mahmoud |
| RECOVERY | Tests after repair | Maintenance + Watchdog |
| NORMAL | Recovery verified | General Manager |

## Episode states

DISCOVERED
→ RESEARCHING
→ VERIFIED
→ EXECUTIVE_REVIEW
→ APPROVED
→ SCRIPTING
→ STORYBOARDING
→ PRODUCING
→ QA
→ PUBLISH_READY
→ PUBLISHED
→ MEASURING
→ LEARNING

Failure from any production state:
→ BLOCKED
→ DIAGNOSING
→ REPAIR_PROPOSAL
→ TESTING
→ either RESUME or ROLLBACK

## Critical invariant
No workflow may move to PUBLISHED unless the publish gate is satisfied and an external publication result is recorded.
