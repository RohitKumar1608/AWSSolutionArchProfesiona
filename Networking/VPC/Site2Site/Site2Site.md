1. A Site-to-Site VPN is a logical connections between a VPC and an on-premise network running over the public internet. The connection is encrypted using IPSec
2. Can be fully HA if it is implemented correctly
3. It is quick to provision, it can be provisioned in less than an hour (contrast to DX)
4. Components involved in creating a VPN connection:
   - VPC
   - Virtual Private Gateway (VGW): it is a gateway object which can be the target of one or more rules in a Route Tables. It can be associated to a single VPC
   - Customer Gateway (CGW): can refer to 2 different things:
       Often is referred to the logical configuration in AWS
       Physical on-premises router which the VPN connects to
   - VPN Connection itself: the connection linking the VGW from the AWS to the CGW 
