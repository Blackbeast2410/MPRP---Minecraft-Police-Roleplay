# Lighting Synchronization

## Problem

Multiple police vehicles may need coordinated emergency lighting without synchronizing every individual light.

## Solution

Use group-level lighting state.

Conceptually:

```java
public record LightingGroupState(
    UUID groupId,
    LightingState state,
    String patternId,
    int phaseOffset,
    TrafficAdvisorMode trafficAdvisor
) {}
```

Each vehicle retains its own physical `LightingPackage`.

The group provides abstract synchronization state.

## Synchronization Modes

- SYNCED
- STAGGERED
- ALTERNATING
- INDEPENDENT

## Pursuit Example

```text
Lighting Group #1042

Primary:   9A21
Secondary: 9A12
Third:     9A15
Supervisor: 9A05
```

The server sends group state changes.

Clients calculate local animation from that state.

Do not copy vehicle A's physical light states into vehicle B.
