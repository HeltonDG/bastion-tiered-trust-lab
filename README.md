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
