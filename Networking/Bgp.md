Key points :- 
1. BGP is the routing protocol - It is the protocol which is used to control how data flow from point A to Point B.
2. BGP is made up from a lot of self managing networks know as Autonomous Systems (AS)
3. Autonomous System could be a large network, collection of routes etc. and is viewed as a black box from BGP perspective.
4. Each AS is allocated a number by IANA, the internet assigned number(ASN).
5. ASNs are 16 bit in length and range from 0 to 65535, the range from 64512 to 65534 is private.
6. ASNs are used by the BGP to identify different entities on the network
7. BGP is designed to be reliable and distributed, and it operates of TCP/179 - It includes error correction and flow control - Reliable.
8. Not automatic, Manually create a peering relationship between two autonomous systems.
9. AS do exchange network topology information between them.
10. BGP is a path-vector protocol: it exchanges the best path to a destination between peers, the path is called ASPATH (Autonomous System Path).
11. iBGP = Internal BGP - Routing within an AS
12. eBGP = External BGP - Routing between AS's








