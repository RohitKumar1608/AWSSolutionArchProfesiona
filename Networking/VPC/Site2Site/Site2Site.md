1. A Site-to-Site VPN is a logical connections between a VPC and an on-premise network running over the public internet. The connection is encrypted using IPSec
2. Can be fully HA if it is implemented correctly
3. It is quick to provision, it can be provisioned in less than an hour (contrast to DX)
4. Components involved in creating a VPN connection:
   - VPC
   - Virtual Private Gateway (VGW): it is a gateway object which can be the target of one or more rules in a Route Tables. It can be associated to a single VPC
   - Customer Gateway (CGW): can refer to 2 different things:
       a) Often is referred to the logical configuration in AWS
       b) Physical on-premises router which the VPN connects to
   - VPN Connection itself: the connection linking the VGW from the AWS to the CGW
  

VGW has physical endpoints in different AZs

Types of VPN Connections 
1. Static
2. Dynamic

Static vs Dynamic VPN:

 Dynamic VPN uses BGP protocol, if customer router does not support BGP, we can not use dynamic VPNs
 Static VPN uses static network configuration: static routes are added to the route tables AWS side, static networks has to be         identified on the VPN connection on-premise side. It is simple, it just uses IPSec, works anywhere, having limitation on terms of HA

 Dynamic VPN uses BGP: allows routing on the fly, allows multiple links to be used at once between the same locations. Allows using HA    available architectures.
 
 Route propagation: if enabled means that routes are added ro the Route Table automatically

Considerations for VPN:

Speed Limitation for VPN: 1.25 Gbps, AWS limitation
Latency considerations: inconsistent, traffic goes through the public internet
Cost: hourly cost for outgoing traffic
VPN can be used for Direct Connect backup or they can be used over the Direct Connect for adding a layer of encryption
