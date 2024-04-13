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

<img width="1440" alt="Screenshot 2024-04-11 at 8 08 33 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/aa7f56ee-d9e2-4c85-95e6-5016e6a4cb62">

Reference link :- 

https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-site-to-site-vpn.html



Advanced Transit Gateway Deep Dive 

1. A TGW default has one RT
2. All attachments use this RT for routing decisions
3. All attachments propagates(add) route to it
4. All attachments can route to all attachments.

Transit Gateway - Isolated Routing
<img width="1440" alt="Screenshot 2024-04-11 at 8 47 37 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/271f2452-fd9a-4301-b4bc-73b9a8ef6ccb">
<img width="1440" alt="Screenshot 2024-04-11 at 8 59 11 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/b2780f09-3d50-4cc6-bcb2-c5dbc14cd2a0">

Advanced VPC Routing
- Subnets are associated with 1 route table (RT) only, no more noe less!
- This route tables is either the main route table from the VPC or a custom route table
- In case of a custom route table association with a subnet, the main route table is disassociated. In case the custom RT is removed, the main RT is associated again with the subnet
- RT can associated with an internet gateway (IGW) or virtual private gateway (VGW)
- IPv4/6 are handled separately within a RT
- Routes send traffic based on a destination to a target
- Route tables have a maximum of 50 static routes and 100 dynamic routes
- When a traffic arrives to an interface (IGW, VGW), it is matched to the relevant route table
- All routes from a route table are evaluated - highest-priority matching is used
- Route tables can contain 2 types of routes:
     - Static routes: added manually by us
     - Propagated routes: added when enabled by us on the VPC or on any individual RT
 
- Evaluation rule for the routes:
   - Longest prefix wins, example /32 wins over /24, /16 or /0. More specific routes always win!
   - Static routes take priority over propagated routes
   - For any routes learned by propagation:
       - DX
       - VPN Static
       - VPN BGP
       - AS_PATH (distance within two logical systems)
    
VPC Routing - Basics

<img width="1440" alt="Screenshot 2024-04-11 at 9 01 02 PM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/19521c6a-c56b-4866-834f-1c71391aa4f7">

##Advanced VPC Routing------------------

CIDR Overlap :-------

<img width="1440" alt="Screenshot 2024-04-12 at 8 05 52 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/6a7947b2-0ab8-44b1-854b-1b34bd3b772f">
<img width="1440" alt="Screenshot 2024-04-12 at 8 12 02 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/400252f1-8e7b-4d50-8037-fc58a0de5a66">

Ingress Routing ------

- All outgoing traffic is routed to a security appliances
- The security appliance is sitting in the public subnet which has a RT assigned to it. This RT sends all unmatched traffic out through    the IGW and anything for the corporate network through the VGW
- Ingress routing allows to assign route tables to gateways (Gateway route tables). Gateway route tables can be attached to internet       gateways or virtual gateways and can be used to take action on inbound traffic (route to a security instance for assessment)

<img width="1440" alt="Screenshot 2024-04-12 at 8 17 07 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/4512e715-b35e-4330-bf6e-28f8e76b0e91">

Accelerated Site to Site VPN :- 

 - Performance enhancement for AWS Site-to-Site VPN that uses the AWS global network, the same network used for Global Accelerator and CloudFront
- Using a classic Site-to-Site VPN, the traffic goes through the public internet. In order to avoid this, some companies use a Site-to-    Site VPN over Direct Connect. Direct Connect offers more better performance, but at a higher cost. Since DX is not an option for         everybody, accelerated Site-to-Site VPN was created to improve performance compared to classic Site-to-Site VPNs

<img width="1440" alt="Screenshot 2024-04-13 at 8 41 52 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/8995fff9-30b0-432e-9003-90c7c7f7a49b">
<img width="1440" alt="Screenshot 2024-04-13 at 8 43 18 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/be4135a3-8145-4c0c-8fc3-4d1a0bb5a59d">

- Accelerated Site-to-Site VPN architecture:

<img width="1440" alt="Screenshot 2024-04-13 at 8 58 09 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/beb5f08c-966f-441f-aa75-b2630932482b">
<img width="1440" alt="Screenshot 2024-04-13 at 9 01 11 AM" src="https://github.com/RohitKumar1608/AWSSolutionArchProfesiona/assets/95314238/18a0c0d5-9e49-47b6-9e09-ccdc3d75c9b3">
