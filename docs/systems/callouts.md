# Callouts

## Architecture

Callouts should be modular and extensible.

Core concepts:

- Callout
- CalloutManager
- CalloutContext
- CalloutState
- CalloutObjective
- CalloutResolution
- CalloutRegistry

## Example Callouts

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

## Design

Callout definitions should be data-driven where practical.

Java handlers should contain behavior that cannot reasonably be expressed as static data.

Avoid putting all callout logic into one manager class.
