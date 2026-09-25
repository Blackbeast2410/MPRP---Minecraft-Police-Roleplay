# Project Structure

Recommended Java structure:

```text
src/main/java/com/yourname/mprp/
├── MPRP.java
├── core/
├── registry/
├── police/
├── vehicle/
├── lighting/
├── siren/
├── radio/
├── cad/
├── dispatch/
├── callout/
├── ai/
├── pursuit/
├── investigation/
├── equipment/
├── weapons/
├── roles/
├── permissions/
├── network/
├── data/
├── platform/
│   └── neoforge/
└── client/
    ├── render/
    ├── screen/
    ├── input/
    └── audio/
```

Resource structure:

```text
src/main/resources/
├── META-INF/
├── assets/mprp/
│   ├── lang/
│   ├── textures/
│   ├── models/
│   ├── sounds/
│   └── shaders/
└── data/mprp/
    ├── departments/
    ├── divisions/
    ├── ranks/
    ├── vehicles/
    ├── lighting/
    ├── sirens/
    ├── radio/
    ├── callouts/
    ├── equipment/
    ├── weapons/
    ├── permissions/
    └── stations/
```

Do not create packages solely to satisfy this diagram. Add them when the corresponding system exists.
