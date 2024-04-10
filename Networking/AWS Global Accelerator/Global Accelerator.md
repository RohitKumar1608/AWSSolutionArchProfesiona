1. Designed to optimize the flow of data from user to AWS infrastructure.
2. Similar to CloudFront, both improve performance when communicating with services hosted in AWS
3. Global Accelerator provides 2 anycast IP addresses. Anycast IP addresses are special type of IP addresses(1.2.3.4 and 4.3.2.1)
4. Normal IP addresses are called unicast IP addresses, these refer to one device in the network.
5. In contrast anycast IP addresses can be used by multiple devices at the same time, the traffic will be routed to the device closest to the source.
6. Global Accelerator uses the AWS Edge Locations. Since multiple locations advertise the given anycast IP addresses, the traffic will be routed to the Edge Location closer to the user
7. AWS has its own dedicated network consisting in fiber links. Edge Locations relay traffic to this network improving performance.

**ClodFront vs Global Accelerator**

1. CloudFront moves the content closer to the customer by caching it on the Edge Location. Global Accelerator moves the customer closer to the service by providing access to the AWS global network
2. Global Accelerator is a network product: works on any TCP/UDP applications not including web apps (HTTP/HTTPS). CloudFront only caches HTTP/HTTPS content.
3. Global Accelerator does not cache anything. It does not understand the HTTP/HTTPS protocol.

Q:- What is anycast and how it route the closest to the user location?
Anycast is a way of routing internet traffic to the closest server out of a group of servers that all share the same IP address. This is useful for things like content delivery networks (CDNs) and domain name system (DNS) services.

Here's a breakdown of how it works:

Multiple servers, one IP address: Imagine multiple data centers around the world, all with the same IP address. This IP address acts like a single entry point for requests.
Routing to the closest server: When a user tries to access a website or service that uses anycast, internet routers consider the location of both the user and the servers. The router then directs the user's request to the server that's geographically closest, resulting in faster loading times.
Benefits: Anycast offers several advantages:
Improved performance: By directing users to the nearest server, anycast reduces latency, meaning webpages and content load faster.
Increased reliability: If one server goes down, traffic can automatically be routed to another server, improving service availability.
DDoS attack mitigation: Anycast distributes traffic across multiple locations, making it harder for attackers to overload a single server with a DDoS attack.
