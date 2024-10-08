
- [OSI Model](#osi-model)
- [Traffic Flow](#traffic-flow)
  - [Type Summary](#type-summary)
- [Component](#component)
  - [VPC](#vpc)
  - [Subnet](#subnet)
  - [Route Table](#route-table)
  - [Gateway](#gateway)
    - [Internet Gateway](#internet-gateway)
    - [NAT Gateway](#nat-gateway)
    - [VPN Gateway](#vpn-gateway)
    - [Customer Gateway](#customer-gateway)
  - [Security Group](#security-group)
  - [Network ACL](#network-acl)


## OSI Model
Open Systems Interconnection Model:
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application


## Traffic Flow
A general traffic flow in AWS VPC would be like:

Client
-> Network ACL
-> Security Group
-> Proxy
-> Firewall
-> Customer Gateway
-> VPN Tunnel
-> VPN Gateway
-> Route Table
-> Subnet
-> Internet Gateway
-> EC2

### Type Summary
| Component        | Type                |
|------------------|---------------------|
| Client           | Software            |
| Network ACL      | Configuration       |
| Security Group   | Configuration       |
| Proxy            | Software / Hardware |
| Firewall         | Software / Hardware |
| Customer Gateway | Software / Hardware |
| VPN Tunnel       | Software / Hardware |
| VPN Gateway      | Software / Hardware |
| Route Table      | Configuration       |
| Subnet           | Configuration       |
| Internet Gateway | Software / Hardware |
| EC2 Instance     | Software            |


## Component

Where each component take effect in OSI model:
| Component | OSI Layer(s)                                                  |
|-----------|---------------------------------------------------------------|
| Proxy     | Layer 7 (Application)                                         |
| Firewall  | Layer 3 (Network), Layer 4 (Transport), Layer 7 (Application) |
| ACL       | Layer 3 (Network), Layer 4 (Transport)                        |
| Gateway   | Layer 3 (Network),  Layer 7 (Application)                     |

### VPC
The Virtual Private Cloud, which is used to define a virtual network where to launch
AWS resources/services.

### Subnet
Subnets are smaller segments within VPC, which helps to organize resources:
- public subnet: accessible from the internet
- private subnet: not directly accessible from the internet

### Route Table
Route Table is like traffic signs that tell data where to go within the VPC.

It defines the paths that network traffic can take, such as how traffic should
flow between subnets or to the internet.

### Gateway
#### Internet Gateway
An Internet Gateway is a bridge that connects VPC to the internet.

It allows resources in __public Subnet__ to communicate with the internet, enabling
things like web servers to serve content to users.

#### NAT Gateway
A NAT (Network Address Translation) Gateway is a service that allows instances in
a __private Subnet__ to access the internet while preventing the internet from
initiating connections to those instances.

It's useful for downloading updates or accessing external APIs from private resources
without exposing them directly to the internet.

#### VPN Gateway
A VPN (Virtual Private Network) Gateway allows to connect local / on-premises network
to the VPC securely over the internet.

It creates a secure tunnel for data to travel between local network and AWS resources.

#### Customer Gateway
A Customer Gateway is the on-premises device (like a router) that connects to the
AWS resources.

### Security Group
Security Group acts as virtual firewall for the resources.

It controls inbound and outbound traffic to the instances, which is used to specify
which IP addresses or protocols are allowed or denied access.

### Network ACL
Network ACL (Access-Control List) is another layer of security that operates at
the subnet level.

It provides a set of rules that apply o all resources in a subnet, allowing or denying
traffic based on IP addresses and protocols.
