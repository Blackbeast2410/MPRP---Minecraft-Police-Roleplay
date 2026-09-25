# Pursuit System

## Purpose

Coordinate suspect vehicle pursuits across vehicle, AI, CAD, radio, lighting, and unit systems.

## Core Concepts

- Pursuit
- PursuitManager
- PursuitUnit
- PursuitState
- PursuitTermination
- Primary
- Secondary
- Supervisor
- Air support
- Spike strip
- Suspect vehicle

## Integration

A pursuit should update relevant systems through events/state changes rather than tightly coupling every subsystem.

Examples:

```text
Pursuit starts
→ CAD update
→ Radio traffic
→ Lighting group created
→ Participating units receive pursuit state
```

When a unit leaves the pursuit, its vehicle lighting returns to independent control.
