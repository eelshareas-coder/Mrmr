# Operating Contract v1

## Decision hierarchy
1. Channel/company mission and safety rules
2. Verified evidence and source requirements
3. General Manager
4. Deputy Manager — Mahmoud during normal review and primary decision authority during manager failover
5. Department agents
6. Production workers

## Two-person safety principle
High-impact actions require two independent checks where possible:
- publishing a sensitive episode;
- changing production policy;
- changing automation permissions;
- deploying self-repair that modifies pipeline behavior.

## Manager health
A manager heartbeat is considered healthy when:
- the manager service responds;
- its state is internally consistent;
- no repeated fatal error threshold is exceeded;
- it has not exceeded the configured inactivity window during an active workflow.

## Failover
When manager health fails:
1. Watchdog records the failure.
2. Current work is frozen at a safe checkpoint.
3. Mahmoud is activated as Acting Manager.
4. Maintenance team diagnoses the manager.
5. The last-known-good state remains authoritative.
6. Recovery is tested before manager control is restored.
7. A post-incident report is written.

## Publishing gate
Publishing requires:
- episode status = PUBLISH_READY;
- QA passed;
- rights/provenance passed;
- metadata present;
- no unresolved critical incident;
- publishing credentials available through an approved integration.

If an external platform connection is unavailable, the system stops at PUBLISH_READY rather than pretending the episode was published.

## Analytics loop
After publication, the analytics department records available first-party metrics and feeds learning signals back into topic selection and episode design. Analytics must not be used to create deceptive engagement or artificial traffic.

## Audit
Every major state transition records:
- timestamp;
- actor/agent;
- episode ID;
- input;
- decision;
- evidence references;
- output;
- error/rollback information where applicable.
