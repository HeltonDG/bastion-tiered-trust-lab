# bastion-tiered-trust-lab
### Designing Controlled Administrative Access Through Bastion Enforcement and Network Trust Boundaries

## Overview

This project documents the design and evolution of a security-focused infrastructure home lab built to model real-world enterprise access patterns.

The environment prioritizes controlled administrative paths, layered trust boundaries, and blast radius reduction over convenience. Rather than extending VPN users directly into the internal network, all privileged access is enforced through a hardened bastion host positioned behind a dedicated network firewall.

The result is an architecture that mirrors mature infrastructure environments where authentication, authorization, and network policy work together to minimize lateral movement and protect critical systems.

## Architectural Objectives

- Enforce a single controlled administrative entry point
- Prevent flat network trust relationships
- Reduce blast radius in the event of host compromise
- Separate external access from privileged infrastructure
- Centralize logging to preserve forensic visibility
- Build a realistic foundation for Active Directory deployment

## Architectural Objectives

- Enforce a single controlled administrative entry point
- Prevent flat network trust relationships
- Reduce blast radius in the event of host compromise
- Separate external access from privileged infrastructure
- Centralize logging to preserve forensic visibility
- Build a realistic foundation for Active Directory deployment

## Design Principles

### Bastion-Governed Access
All administrative traffic is required to traverse a hardened RHEL 9 bastion host. Internal servers are not directly reachable from the VPN.

### Network-Enforced Trust Boundaries
pfSense operates as the primary policy enforcement point, ensuring that access between zones is intentional and auditable.

### No Flat VPN
Remote users are never dropped directly into the internal server network.

### Progressive Trust Model
Trust increases gradually as traffic moves inward:

VPN → Firewall → Bastion → Internal Servers

### Forensic Resilience
Logs are forwarded to a centralized logging server to prevent attackers from erasing operational history.

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

## Controlled Administrative Path

Remote Administrator  
→ WireGuard VPN  
→ pfSense Firewall  
→ Bastion Host  
→ Internal Servers  

Internal systems do not accept direct connections from the VPN.

## Security Decisions

Several deliberate constraints were implemented:

- Internal servers have no bridged NICs
- SSH access is restricted to bastion-originated traffic
- VPN clients cannot laterally scan the server network
- Administrative access is identity-driven rather than network-convenience driven
- Logging infrastructure resides deeper within the trust boundary

## Technology Stack

- **Firewall:** pfSense  
- **VPN:** WireGuard  
- **Bastion:** RHEL 9  
- **Logging:** rsyslog  
- **Virtualization:** VMware  
- **Planned Identity Layer:** Active Directory  

## Planned Enhancements

This architecture intentionally serves as a foundation for deeper identity-driven security controls.

Upcoming focus areas include:

- Active Directory deployment
- Tiered administrative model
- Group Policy enforcement
- Expanded centralized logging
- Privileged access strategy

## Closing Notes

This lab is not designed for feature accumulation but for architectural clarity.

Each design decision favors operational predictability, security layering, and realistic administrative flow over unnecessary complexity.

The goal is to continuously refine an environment that reflects how modern infrastructure is secured and operated.
