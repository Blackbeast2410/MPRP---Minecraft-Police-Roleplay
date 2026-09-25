# Emergency Lighting System

## Purpose

Provide realistic, configurable emergency lighting for police vehicles.

## Major Components

- EmergencyLightingController
- LightHead
- LightGroup
- LightingState
- LightingPattern
- PatternStep
- TrafficAdvisor
- TakeDownController
- AlleyLightController
- SceneLighting
- LightingPackage
- LightingGroupManager
- UnitLightingGroup
- PursuitLightingGroup

## States

- OFF
- CRUISE
- WARNING
- EMERGENCY
- PURSUIT
- SCENE
- TRAFFIC_ADVISOR

## Patterns

- Alternating
- Simultaneous
- Left-to-right
- Right-to-left
- Center-out
- Outside-in
- Flash
- Double flash
- Quad flash

## Additional Functions

- Take-down illumination
- Left/right alley lights
- Scene lighting
- Traffic Advisor
- Cruise lighting

## Rendering

The server stores authoritative abstract lighting state.

The client renders:

- Flash animation
- Emissive effects
- Glow
- Dynamic visual effects
- Reflections where supported

Do not synchronize every physical light every tick.
