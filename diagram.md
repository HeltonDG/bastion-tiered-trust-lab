                                      Internet
                                          |
                                   Public IP
                                          |
                                +----------------------+
                                |    Edge Router       |
                                |----------------------|
                                | NAT / Gateway        |
                                | No Admin Exposure    |
                                |                      |
                                | LAN: 172.16.50.1/24  |
                                +----------+-----------+
                                           |
                              Untrusted Transit Network
                                   172.16.50.0/24
                                           |
                                           |
                                    +------+------+
                                    |   pfSense   |
                                    |-------------|
                                    | Firewall    |
                                    | WireGuard   |
                                    | Routing     |
                                    +------+------+
                                           |
                              WireGuard VPN (10.200.77.0/24)
                                           |
                                  =================
                                   TRUST BOUNDARY
                                  =================
                                           |
                                           |
                             Secure Enclave Network
                                   10.10.20.0/24
                                           |
                    +----------------------+----------------------+
                    |                                             |
                    |                                             |
            +-------+--------+                           +--------+--------+
            |     jump01     |                           |      log01      |
            |----------------|                           |-----------------|
            | RHEL 9 Bastion |                           | Central Logging |
            |                |                           | rsyslog         |
            | 10.10.20.10    |                           | 10.10.20.20     |
            +-------+--------+                           +-----------------+
                    |
                    | Controlled Administrative Access Only
                    |
            +-------+--------+
            |      srv01     |
            |----------------|
            | Internal Server|
            | 10.10.20.11    |
            +----------------+


====================== ADMINISTRATIVE FLOW ======================

Remote Administrator
        |
        | WireGuard VPN
        | (10.200.77.0/24)
        v
pfSense Firewall
        |
        v
jump01 (Bastion)
        |
        v
Internal Servers


====================== SECURITY MODEL ======================

✔ VPN users are NEVER dropped into the server network  
✔ Bastion is the single administrative choke point  
✔ Firewall enforces all trust boundaries  
✔ Internal servers have no exposure to transit networks  
✔ Logging resides deeper inside the enclave  
✔ Administrative trust increases progressively inward


====================== TRUST TIERS ======================

LOW TRUST
    VPN Clients

CONTROLLED TRUST
    Bastion (jump01)

HIGH TRUST
    Internal Servers + Logging

FUTURE TIER-0
    Active Directory
