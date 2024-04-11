1. It is a network transit hub which connects VPCs to each other and to on-premise networks using Site-to-Site VPNs and Direct Connects
2. significantly reduces network complexity
3. Single network object - HA and Scalable
4. Attachments: we create attachments in order for the TGW to connect to VPCs and on-premise networks. Valid attachments are:
     - VPC attachments
     - Site-to-Site VPN attachments
     - Direct Connect Gateway attachments
5. Attachments are configured in each subnet of the connected VPCs
6. We can also peer transit gateways across cross regions and/or cross accounts
7. We can also attach transit gateways to the DX connections
8. Transit Gateway Considerations:
     - Supports transitive routing: single transit gateway with multiple attachments using route tables
     - Can be used to create global networks with peering
     - We can share transit gateways using AWS RAM
     - Transit Gateways offer less complex architectures compared to VPC peering solutions

Reference link :- 

https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-site-to-site-vpn.html
