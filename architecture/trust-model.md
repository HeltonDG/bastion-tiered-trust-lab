# Trust Model

The lab is structured around progressive trust escalation rather than implicit network trust.

Zones are defined by their exposure level and operational sensitivity:

- External / VPN Zone — lowest trust  
- Bastion Tier — controlled administrative boundary  
- Core Infrastructure — highest trust  

Movement between zones requires deliberate firewall policy.
