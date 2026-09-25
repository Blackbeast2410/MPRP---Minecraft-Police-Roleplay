# Investigation and Evidence

## Core Concepts

- Case
- Evidence
- EvidenceChain
- ArrestRecord
- Citation
- Report
- PersonRecord
- VehicleRecord

## Typical Flow

```text
Call
→ Incident
→ Evidence / Arrest
→ Case
→ Report
→ Supervisor Review
→ Closed
```

## Evidence

Evidence should support a lifecycle such as:

```text
Collected
→ Bagged
→ Labeled
→ Submitted
→ Stored
→ Analyzed
→ Linked to Case
```

Persistent evidence must survive server restarts when the gameplay design requires it.
