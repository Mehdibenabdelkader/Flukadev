---
title: "Load Balancing : A piece of cake"
date: 2023-11-04T08:55:23+01:00
draft: false
---

if modern infrastructure design was a birthday party, Load balancing would be sharing a cake, and you can't have a party without cake ofc  (I am sorry I can't help it I love these analogies), ensuring high availability and efficient distribution of incoming traffic across multiple servers or instances, in other words making sure that everyone gets a slice. Amazon Web Services (AWS) provides two popular load balancer services: the Application Load Balancer (ALB) and the Network Load Balancer (NLB). They both play a crucial role in distributing traffic, yet they serve different purposes and exhibit many differences.


### Application Load Balancer (ALB)

- **Layer 7 Load Balancer:** ALB operates at the application layer (Layer 7) of the OSI model. This means it understands and routes traffic based on the content of the data being transmitted. It's ideal for handling HTTP traffic because it can look inside the data packets to see what's being requested.

- **Content-Based Routing:** ALB uses content-based routing to decide where to send incoming requests. It can look at things like the website's address (host), the specific path on the website, or the headers in the request to figure out where the request should go. This is very useful for modern web applications and microservices because different parts of the application may handle different types of requests.

- **Advanced Routing Rules:** ALB supports advanced routing rules. For example, if you have a website that serves both pictures and videos, you can set up ALB to send picture requests to one group of servers and video requests to another. It can even route requests based on the specific URLs requested.

- **Target Group:** ALB forwards incoming traffic to a target group. A target group is a collection of servers or instances that can handle the incoming requests. This group can include various types of targets, such as EC2 instances, IP addresses, or even AWS Lambda functions.

- **Health Checks:** ALB regularly checks the health of the targets in the target group. If a target is not responding properly, ALB will stop sending traffic to it until it recovers. This ensures that traffic only goes to healthy servers, improving the reliability of your application.

- **WebSockets and HTTP/2 Support:** ALB is compatible with modern web technologies like WebSockets and HTTP/2. WebSockets allow for real-time, interactive communication, while HTTP/2 improves the efficiency of loading web pages. ALB can handle traffic using these technologies effectively.


### Network Load Balancer (NLB)

- **Layer 4 Load Balancer:** NLB operates at the transport layer (Layer 4) of the OSI model. It doesn't look inside the data packets; it simply forwards them based on information like source and destination IP addresses and port numbers. This makes it suitable for handling a wide range of traffic, including TCP, UDP, and TLS, regardless of the specific content being transmitted.

- **Ultra-Low Latency:** NLB is designed for applications that require extremely fast and low-latency responses. It can handle a high volume of incoming requests and deliver them quickly. This is important for applications like online gaming, where responsiveness is critical.

- **Static IP Addresses:** NLB provides static IP addresses that remain constant over time. This is important for applications that require a fixed endpoint for clients to connect to. It's particularly useful when you have clients that need to whitelist IP addresses for security reasons.

- **Support for IP Target Types:** NLB can forward traffic to a variety of target types, including IP addresses and Elastic Network Interfaces (ENIs). This flexibility allows you to use NLB in various use cases, such as directing traffic to on-premises servers or other AWS services.


### Application Load Balancer (ALB) Use Cases:

- **Web Applications:** ALB is a fantastic choice for web applications that rely on HTTP and HTTPS traffic. It can route requests based on URL paths or hostnames. Imagine you have a shopping website with different sections like electronics, clothing, and groceries. ALB can route requests for each category to the right set of servers. So, when you click on electronics, ALB ensures your request goes to the electronics servers, and when you click on clothing, it directs you to the clothing servers.
Microservices:

- **Microservices:** ALB's content-based routing is ideal for routing requests to different microservices based on request attributes. Suppose you have an e-commerce app that includes user authentication, product search, and payment processing. ALB can send requests for authentication to the authentication microservice, product searches to the search microservice, and payments to the payment microservice.
API Gateways:

- **API Gateways:** If you're building an API gateway, ALB's advanced routing rules can help you direct requests to specific backend services. If you're building an API gateway for a mobile app, you might have different backend services for user profiles, notifications, and messaging. ALB can look at the incoming requests and send them to the appropriate service. For example, user profile requests go to the user profile service, and messaging requests go to the messaging service.

### Network Load Balancer (NLB) Use Cases:

- **High-Performance Applications:** NLB is excellent for applications that demand ultra-low latency and high throughput, such as online gaming or streaming services. In an online game, players make moves, and those moves need to be quickly processed on game servers. NLB makes sure that these moves are delivered to the game servers as fast as possible, reducing any delays in the game.
TCP/UDP Workloads:

- **TCP/UDP Workloads:** NLB shines when handling non-HTTP traffic like gaming, VoIP, or any protocol that operates at the transport layer. In VoIP applications, when you're on a call, your voice data needs to be delivered without delay. NLB's low latency ensures that your voice reaches the other person almost instantly, resulting in clear and real-time communication.

- **IP Whitelisting:** Applications that rely on IP whitelisting for security can benefit from NLB's static IP address and source IP preservation capabilities. In a corporate environment, the company's servers may only accept connections from known office IP addresses for security reasons. NLB's static IP addresses can help ensure that only authorized devices can access the services.


## Conclusion

In summary, both the Application Load Balancer (ALB) and the Network Load Balancer (NLB) are essential AWS services that serve different purposes. Choosing between them should be based on your specific application requirements, such as the type of traffic, performance needs, and routing rules. By understanding these key principles, you can make sure your applications gets their favourite cake at the right time.


