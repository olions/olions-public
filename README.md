# olions-public
public assets

```mermaid
graph TD
    subgraph Azure Subscription
        subgraph Hub VNet (Shared Services & Connectivity)
            A[Azure Firewall] --> B(DMZ Subnet)
            B --> C(Gateway Subnet)
            C -- VPN/ExpressRoute --> D(On-Premises Network)
            B --> E(Shared Services Subnet)
            E --> F(Azure AD Domain Services, DNS, Monitoring)
        end

        subgraph Spoke VNet 1 (Application A)
            G(Application A Subnet 1)
            H(Application A Subnet 2)
        end

        subgraph Spoke VNet 2 (Application B)
            I(Application B Subnet 1)
            J(Application B Subnet 2)
        end
    end

    Hub VNet --- Peering --- Spoke VNet 1
    Hub VNet --- Peering --- Spoke VNet 2

    G -- NSG --> H
    I -- NSG --> J
    E -- NSG --> G
    E -- NSG --> I
```
