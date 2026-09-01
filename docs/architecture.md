# Architecture

## Traditional AWS Architecture

```mermaid
flowchart LR
    USER[User / Browser]

    subgraph AWSVPC[AWS VPC]
        subgraph PUB[Public Subnet]
            CTRL[Ansible Control Node]
            WEB[Java Web Server]
            NAT[NAT Gateway]
        end

        subgraph PRIV[Private Database Subnet]
            MYSQL[(MySQL)]
        end

        IGW[Internet Gateway]
    end

    USER -->|8080| WEB
    CTRL -->|SSH| WEB
    CTRL -->|SSH private IP| MYSQL
    WEB -->|3306| MYSQL

    MYSQL --> NAT
    NAT --> IGW
    WEB --> IGW