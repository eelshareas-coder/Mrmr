# Maintenance & Self-Repair Playbook v1

## Detection
The maintenance team watches:
- workflow failures;
- missing expected artifacts;
- malformed episode records;
- broken links between pipeline stages;
- repeated job failures;
- stale manager heartbeat;
- failed tests.

## Repair loop
1. Capture incident.
2. Freeze the affected stage.
3. Identify the smallest failing component.
4. Preserve logs and last-known-good state.
5. Generate a repair proposal.
6. Apply repair only in an isolated test context.
7. Run automated tests.
8. If tests fail: rollback and escalate.
9. If tests pass: mark repair candidate.
10. Require the appropriate approval gate before production deployment.
11. Record post-repair verification.

## Rollback
Rollback must restore the last-known-good version/state without deleting audit records.

## Forbidden repair behavior
- changing access controls to make a repair work;
- disabling safety/QA gates;
- deleting incident evidence;
- publishing while a critical incident is unresolved;
- recursively modifying the repair system without review.

## Manager recovery
The manager is treated like a software service for continuity purposes:
- heartbeat;
- health check;
- checkpoint;
- recovery test;
- controlled return to service.

The maintenance team does not make editorial decisions. Mahmoud owns continuity decisions when the manager is unavailable.
