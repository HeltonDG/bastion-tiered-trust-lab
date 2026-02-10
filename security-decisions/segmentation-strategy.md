## Security Decisions

Several deliberate constraints were implemented:

- Internal servers have no bridged NICs
- SSH access is restricted to bastion-originated traffic
- VPN clients cannot laterally scan the server network
- Administrative access is identity-driven rather than network-convenience driven
- Logging infrastructure resides deeper within the trust boundary

# Segmentation Strategy

Segmentation is implemented to reduce lateral movement and contain potential compromise.

Key strategies include:

- Bastion-only administrative access
- Isolation of internal servers from direct VPN reachability
- Centralized logging positioned deeper within the trust boundary
- Firewall-enforced policy between tiers

The design favors simplicity while preserving strong security posture.

