## Architecture Evolution

This lab was intentionally developed in phases to reflect how real infrastructure matures over time.

### Phase 1 — Bastion Foundation
The initial design enforced administrative access through a jump host while isolating internal servers on a non-bridged network.

### Phase 2 — Tiered Trust Architecture
The environment was later redesigned to introduce a dedicated network firewall, allowing trust boundaries to be enforced at the network layer rather than relying solely on host-level controls.

This transition significantly improved:

- Traffic visibility  
- Policy enforcement  
- Segmentation  
- Blast radius control  

The current architecture reflects a defense-in-depth approach aligned with enterprise infrastructure practices.
