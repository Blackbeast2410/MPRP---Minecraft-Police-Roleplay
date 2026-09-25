# Singleplayer and Multiplayer Architecture

## Singleplayer

Singleplayer provides the gameplay systems without requiring human network roles.

Examples:

- Police vehicles
- Lighting
- Sirens
- Equipment
- Weapons
- MDT
- Stations
- NPC callouts
- Suspect AI

There is no requirement to simulate a human dispatcher.

## Multiplayer

Multiplayer adds real human roles:

- Officers
- Dispatchers
- Supervisors
- Command
- Civilian/administrative staff

Systems such as CAD and radio use actual network communication.

## Shared Interfaces

Where practical, shared interfaces should allow different implementations.

Example:

```text
DispatchService
├── LocalDispatchService
└── NetworkDispatchService
```

The exact class structure may evolve with implementation.

## Runtime Mode

Runtime mode should be determined by the actual environment rather than scattered boolean checks.

Do not duplicate entire gameplay systems simply because the game is running in singleplayer.
