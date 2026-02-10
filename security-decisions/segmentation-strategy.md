## Security Decisions

Several deliberate constraints were implemented:

- Internal servers have no bridged NICs
- SSH access is restricted to bastion-originated traffic
- VPN clients cannot laterally scan the server network
- Administrative access is identity-driven rather than network-convenience driven
- Logging infrastructure resides deeper within the trust boundary
