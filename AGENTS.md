# MPRP AGENTS.md

## 1. Project Identity

MPRP (Minecraft Police Roleplay) is a large-scale, modular police roleplay framework for Minecraft.

The project is inspired by LSPDFR and real-world law enforcement operations.

MPRP aims to provide:

- Police departments and organizational structures
- Officers, ranks, assignments, and units
- Realistic police vehicles
- Emergency lighting systems
- Sirens and police radio
- CAD and dispatch
- Dynamic callouts
- NPC and suspect AI
- Vehicle pursuits
- Investigations and evidence
- Arrests, citations, and reports
- Functional police stations
- MDT systems
- Multiplayer police roleplay
- Data-driven content and extensibility

MPRP is a long-term software project. Do not treat it as a collection of isolated scripts or examples.

---

## 2. Technology Stack

Current target:

- Minecraft: 1.21.1
- Mod Loader: NeoForge
- Java: 21
- Build System: Gradle
- Version Control: Git

Do not change the Minecraft version, NeoForge version, Java version, or Java version requirements without explicit approval.

---

## 3. Engineering Philosophy

Prioritize:

1. Maintainability
2. Extensibility
3. Performance
4. Multiplayer correctness
5. Singleplayer compatibility
6. Clear separation of responsibilities
7. Data-driven content
8. Testability
9. Minimal unnecessary dependencies

Prefer simple and understandable solutions over unnecessary abstraction.

Do not introduce architecture solely because it appears sophisticated.

---

## 4. Before Editing Code

Before implementing a non-trivial feature:

1. Inspect the repository.
2. Identify the existing architecture.
3. Search for related classes and interfaces.
4. Read relevant documentation under `/docs`.
5. Check existing implementations.
6. Identify client/server responsibilities.
7. Check existing networking patterns.
8. Check existing data and persistence mechanisms.
9. Determine whether the requested feature already partially exists.

Do not immediately rewrite existing systems.

Do not assume an implementation is missing simply because its class name is not obvious.

---

## 5. Scope Control

Only modify files required for the current task.

Do not:

- Rewrite unrelated systems.
- Replace working architecture without justification.
- Rename large groups of classes unnecessarily.
- Remove functionality without approval.
- Introduce unrelated refactors.
- Change public APIs silently.
- Reformat unrelated files.
- Replace existing implementations merely because another approach is preferred.

Keep changes focused and reviewable.

---

## 6. Server Authority

MPRP multiplayer gameplay must be server authoritative.

The server is responsible for authoritative state such as:

- Officer state
- Unit state
- Calls
- CAD state
- Assignments
- Pursuits
- Arrests
- Evidence
- Permissions
- Vehicle gameplay state
- Lighting state
- Siren state
- Radio state

Clients must not be trusted to directly determine authoritative gameplay state.

Client requests must be validated by the server.

---

## 7. Client Responsibilities

The client should primarily handle:

- Rendering
- Visual effects
- Lighting animation
- Audio
- GUI
- Input
- Local presentation

Do not move authoritative gameplay logic to the client simply because it is easier to implement.

Visual and audio effects should remain client-side whenever practical.

---

## 8. Singleplayer Compatibility

MPRP must support singleplayer.

Singleplayer should provide:

- Police vehicles
- Emergency lighting
- Sirens
- Police equipment
- Weapons
- Police stations
- MDT functionality
- Local gameplay systems
- Callouts and NPC interactions

Do not fabricate fake human multiplayer communication unless the feature explicitly requires an offline simulation.

Shared interfaces should be used where practical so that singleplayer and multiplayer implementations can coexist without duplicating the entire architecture.

---

## 9. Multiplayer

Multiplayer should support real human roles including:

- Police Officer
- Dispatcher
- Supervisor
- Command
- Civilian / Administrative Staff

Multiplayer systems include:

- CAD
- Radio
- Unit status
- Dispatch
- Pursuits
- Shared incidents
- Role permissions

Use server-authoritative state and event-driven synchronization.

---

## 10. Networking

Prefer event-driven networking.

Send state changes and meaningful events rather than continuously synchronizing complete state.

Avoid:

- Full state synchronization every tick
- Per-light network packets every tick
- Unnecessary polling
- Repeated broadcasts of unchanged state
- Large unnecessary packets

Typical client-to-server requests may include:

- Toggle lights
- Change lighting mode
- Toggle siren
- Radio transmission
- Change radio channel
- Update unit status
- Accept a call
- Request backup
- Interact with CAD
- Interact with MDT

Typical server-to-client updates may include:

- Lighting state
- Siren state
- Radio transmissions
- CAD updates
- Call assignments
- Unit status
- Pursuit state

---

## 11. Performance

Performance is a major project requirement.

Avoid unnecessary:

- Global entity scans every tick
- Full network synchronization
- Expensive pathfinding every tick
- Repeated data loading
- Excessive object allocation in hot loops
- Unbounded AI processing
- Unnecessary client rendering work

Prefer:

- Events
- Cached state
- Timers
- State machines
- Incremental updates
- Data-driven definitions
- Controlled update intervals

Do not optimize based purely on assumptions when profiling can provide evidence.

---

## 12. Data-Driven Design

Separate content from core logic whenever practical.

Data-driven systems should include:

- Departments
- Divisions
- Ranks
- Vehicles
- Lighting packages
- Siren packages
- Radio configuration
- Callouts
- Equipment
- Weapons
- Permissions
- Stations

Adding a new vehicle or lighting package should not require rewriting the core system.

---

## 13. Police Organization

MPRP uses a hierarchical organizational model.

The architecture should support:

- Department
- Bureau
- Division
- Station
- Watch
- Beat
- Officer
- Rank
- Assignment
- Unit

The initial reference organization is LAPD-style, but the system must remain configurable enough to support other departments.

Do not hardcode the entire organizational structure into gameplay logic.

---

## 14. Unit System

Units should support states such as:

- OFF_DUTY
- AVAILABLE
- EN_ROUTE
- ON_SCENE
- BUSY
- TRANSPORTING
- AT_HOSPITAL
- AT_STATION
- OUT_OF_SERVICE

Do not assign BUSY units unless an explicit override exists.

Example unit:

9A21
Valley Division
Watch II
Beat 0913

Unit state should be authoritative on the server.

---

## 15. Vehicle System

Vehicle architecture should separate:

- Vehicle entity
- Vehicle definition
- Vehicle model
- Vehicle equipment
- Handling
- Emergency lighting
- Siren
- Radio
- MDT
- Inventory

Important concepts may include:

- `PoliceVehicle`
- `VehicleDefinition`
- `VehicleState`
- `VehicleEquipment`
- `VehicleRegistry`

Do not hardcode individual vehicle models into the core vehicle implementation.

Use data-driven vehicle definitions.

---

## 16. Vehicle Assets

Vehicle models and visual assets are separate from gameplay logic.

A vehicle should be able to reference:

- Model
- Texture
- Lighting package
- Siren package
- Handling package
- Equipment configuration

Asset names must not be used as a substitute for gameplay state.

Do not include third-party copyrighted assets unless their distribution rights are clear.

---

## 17. Emergency Lighting

Emergency lighting is a major MPRP subsystem.

Important concepts include:

- `EmergencyLightingController`
- `LightHead`
- `LightGroup`
- `LightingState`
- `LightingPattern`
- `PatternStep`
- `TrafficAdvisor`
- `TakeDownController`
- `AlleyLightController`
- `SceneLighting`
- `LightingPackage`
- `LightingGroupManager`
- `UnitLightingGroup`
- `PursuitLightingGroup`

Supported states should include:

- OFF
- CRUISE
- WARNING
- EMERGENCY
- PURSUIT
- SCENE
- TRAFFIC_ADVISOR

Supported visual functions may include:

- Emergency warning lights
- Traffic Advisor
- Take-down lights
- Alley lights
- Scene lighting
- Cruise lighting

---

## 18. Lighting Patterns

The lighting system should support reusable patterns such as:

- Alternating
- Simultaneous
- Left-to-right
- Right-to-left
- Center-out
- Outside-in
- Flash
- Double flash
- Quad flash

Patterns should be data-driven where practical.

Do not hardcode every vehicle's flash sequence into Java classes.

---

## 19. Lighting Synchronization

Multiple vehicles must be able to synchronize their emergency lighting.

Do not copy individual light states from one vehicle to another.

Use group-level state.

A lighting group may contain:

- Group ID
- Lighting state
- Pattern ID
- Synchronization mode
- Phase information
- Traffic Advisor state

Supported synchronization concepts include:

- SYNCED
- STAGGERED
- ALTERNATING
- INDEPENDENT

Each vehicle keeps its own `LightingPackage`.

The group controls abstract synchronization state.

Vehicles render their own physical lights locally.

Use phase offsets when appropriate to avoid unrealistic perfectly synchronized flashing.

Pursuit groups should be able to synchronize:

- Primary
- Secondary
- Additional units
- Supervisor
- Traffic Advisor
- Scene lighting

When a vehicle leaves a pursuit group, it should return to independent lighting control.

---

## 20. Siren System

Siren logic must remain separate from lighting logic.

Support:

- Wail
- Yelp
- Phaser
- Horn
- Siren patterns
- Siren state

Do not automatically couple siren activation to emergency lighting activation.

Audio should be handled client-side whenever possible.

---

## 21. Radio System

The radio system should support:

- Channels
- Push-to-talk
- Transmission state
- Priority traffic
- Emergency traffic
- Volume
- Squelch

Emergency traffic must be capable of overriding normal radio traffic.

Radio communication in multiplayer should be networked.

Singleplayer must not pretend that a human dispatcher exists unless an explicit offline simulation is implemented later.

---

## 22. CAD and Dispatch

CAD is a major multiplayer subsystem.

Core concepts include:

- `Call`
- `UnitRegistry`
- `UnitAssignment`
- `BOLO`
- `Warrant`
- `Incident`

Typical call lifecycle:

CREATED
→ QUEUED
→ DISPATCHED
→ ACKNOWLEDGED
→ EN_ROUTE
→ ON_SCENE
→ INVESTIGATING
→ CLEARED
→ CLOSED

CAD state must be server authoritative.

Dispatch must respect unit availability and status.

---

## 23. Callouts

Callouts should use a modular architecture.

Important concepts include:

- `Callout`
- `CalloutManager`
- `CalloutContext`
- `CalloutState`
- `CalloutObjective`
- `CalloutResolution`
- `CalloutRegistry`

Examples include:

- Traffic Stop
- Suspicious Vehicle
- Suspicious Person
- Burglary
- Shoplifting
- Welfare Check
- Domestic Disturbance
- Vehicle Collision
- Stolen Vehicle
- Robbery
- Shots Fired
- Armed Suspect
- Officer Needs Help
- Pursuit

Callout content should be data-driven where practical.

---

## 24. AI

NPC and suspect AI should use controlled state machines and events.

Avoid unrestricted expensive logic every tick.

AI should be designed around states, transitions, goals, and controlled update intervals.

AI behavior must not introduce global scans or expensive pathfinding without justification.

---

## 25. Pursuit System

Pursuits must integrate with:

- Vehicles
- CAD
- Radio
- Lighting
- Sirens
- AI
- Unit assignments
- Supervisors

Important concepts include:

- Primary
- Secondary
- Supervisor
- Air support
- Spike strips
- Suspect vehicle
- Pursuit state
- Pursuit termination
- Arrest
- Crash

Pursuit lighting must use `PursuitLightingGroup` rather than directly copying individual light states between vehicles.

---

## 26. Investigation and Evidence

Investigation systems may include:

- Cases
- Evidence
- Evidence chain
- Arrest records
- Citations
- Reports
- Person records
- Vehicle records

Typical flow:

Call
→ Incident
→ Evidence / Arrest
→ Case
→ Report
→ Supervisor Review
→ Closed

Evidence state must be persistent where appropriate.

---

## 27. Police Stations

Police stations should function as gameplay hubs.

Potential systems include:

- Front desk
- Briefing room
- Locker room
- Armory
- Garage
- Dispatch room
- Watch commander office
- Evidence room
- Records
- Interview room
- Booking
- MDT terminals

Do not implement every station feature in a single class.

---

## 28. Roles and Permissions

Do not use Minecraft OP status as the primary MPRP permission system.

MPRP should use its own role and permission architecture.

Possible roles include:

- Police Officer
- Dispatcher
- Supervisor
- Command
- Records
- Evidence Technician
- Crime Analyst
- Forensic Technician
- Property Clerk
- Civilian Staff

Permissions should be data-driven where practical.

---

## 29. Persistence

Persistent state must survive server restarts where required.

Use appropriate Minecraft persistence mechanisms for:

- Player data
- Officer data
- Entity data
- Vehicle data
- Block entities
- Item data

Do not keep required persistent state only in runtime memory.

---

## 30. Dependencies

Do not add dependencies without a clear reason.

Before adding a major dependency:

1. Check whether NeoForge or Minecraft already provides the functionality.
2. Check maintenance status.
3. Check license compatibility.
4. Check client/server implications.
5. Check long-term maintenance cost.

Major dependencies require explicit approval.

---

## 31. Error Handling

Do not silently suppress important errors.

Prefer:

- Clear logging
- Validation
- Safe fallback behavior
- Explicit error states

Do not hide exceptions merely to make the build succeed.

---

## 32. Testing

After significant changes:

1. Run the appropriate Gradle build.
2. Fix compiler errors.
3. Fix runtime errors.
4. Test the affected feature.
5. Test client/server behavior where applicable.
6. Test singleplayer compatibility.
7. Test multiplayer synchronization where relevant.
8. Check for obvious performance regressions.

Do not claim a feature is complete without testing it.

---

## 33. Git Workflow

Use focused Git commits.

Recommended workflow:

Create feature branch
→ Implement
→ Build
→ Test
→ Review diff
→ Commit

Examples:

- `feat: add police unit system`
- `feat: add emergency lighting controller`
- `feat: add pursuit lighting groups`
- `fix: prevent busy units from receiving calls`
- `refactor: separate vehicle definition from entity logic`
- `docs: update lighting architecture`

Do not combine unrelated features into a single commit.

---

## 34. Documentation

Major systems must have documentation under `/docs`.

Documentation should explain:

- Purpose
- Architecture
- Responsibilities
- Public interfaces
- Data formats
- Networking
- Persistence
- Extension points
- Important design decisions

Keep documentation synchronized with significant architectural changes.

---

## 35. Unclear Requirements

If a requirement affects:

- Architecture
- Networking
- Persistence
- Public APIs
- Security
- Permissions
- Major gameplay behavior

and the requirement is ambiguous, do not silently make a major architectural decision.

First inspect the existing design.

If a safe interpretation exists, prefer the least disruptive solution.

If the decision has long-term consequences, ask for clarification.

---

## 36. Standard Engineering Workflow

Every significant task should follow:

1. Understand the requirement.
2. Inspect the repository.
3. Read relevant documentation.
4. Identify affected systems.
5. Plan the implementation.
6. Implement the smallest appropriate change.
7. Build.
8. Test.
9. Review the diff.
10. Update documentation if required.
11. Commit.

Do not jump directly from a feature request to a large rewrite.

---

## 37. Definition of Done

A task is complete only when:

- The project compiles.
- Relevant tests pass.
- Client starts when applicable.
- Server starts when applicable.
- The requested feature works.
- Client/server boundaries are correct.
- Network behavior is validated where applicable.
- Persistence is considered where applicable.
- No obvious unnecessary tick or network overhead was introduced.
- Existing functionality was not unnecessarily broken.
- Documentation is updated when required.
- The Git diff is focused and reviewable.

---

## 38. Agent Behavior

When working on MPRP:

- Act as an engineer working inside an existing codebase.
- Inspect before editing.
- Prefer incremental changes.
- Preserve existing architecture unless there is a clear reason to change it.
- Explain important architectural decisions.
- Do not fabricate APIs or classes that do not exist.
- Do not claim tests passed unless they were actually run.
- Do not claim a feature works without verification.
- Do not modify unrelated files.
- Do not replace project decisions with personal preferences.

The goal is to help build MPRP as a maintainable long-term project, not merely to make the current task compile.
