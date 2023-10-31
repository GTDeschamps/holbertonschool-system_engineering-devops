# README of  "Web Infrastructure" Project

# 0. Simple web stack

![Web Stack](https://github.com/GTDeschamps/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/0-simple_web_stack.png?raw=true)

## Differences between Server, Web Server, Application Server and Database Server:

Server, Web server, Application server, and Database server are different types of servers used in the context of computer networks and web applications. Here's an overview of the key differences between them:

1/ **Server**:

A server is a computer or a software program that provides services or resources to other computers or clients over a network. Servers can handle various types of requests and are responsible for processing and responding to those requests.

2/ **Web Server**:

A web server is a specific type of server that is designed to handle HTTP (Hypertext Transfer Protocol) requests and serve web content to clients, typically web browsers. Web servers store and deliver web pages, images, scripts, and other web-related resources to users when they access a website. Popular web servers include Apache, Nginx, and Microsoft Internet Information Services (IIS).

3/ **Application Server**:

An application server is a server specifically designed to run applications and provide the necessary runtime environment for these applications. Application servers are used to host and execute web applications, including business logic and application-specific processes. They often interact with databases and can perform tasks like authentication, session management, and load balancing. Examples of application servers include Tomcat, WildFly (formerly JBoss), and Microsoft ASP.NET.

4/ **Database Server**:

A database server is a specialized server designed to store, manage, and provide access to databases. Database servers are responsible for handling database-related operations, such as data storage, retrieval, querying, and data manipulation. They may use database management systems (DBMS) like MySQL, PostgreSQL, Microsoft SQL Server, Oracle, or MongoDB to manage the data efficiently. Application servers and web servers often interact with database servers to access and manipulate data as needed for web applications.

_In summary, a server is a broad term that refers to a computer or software that provides services, while a web server serves web content over HTTP. An application server hosts and manages web applications, providing a runtime environment for them, and a database server stores, manages, and provides access to databases. These servers often work together in web applications, with web servers handling client requests, application servers executing application logic, and database servers managing data storage and retrieval._

## type of DNS record "www" is in www.foobar.com:

The "www" in a domain like "www.foobar.com" is typically a subdomain, and it is represented as a "CNAME" (Canonical Name) DNS record. The CNAME record is used to alias one domain name to another. In this case, "www" is an alias for the root domain "foobar.com."

When a user enters "www.foobar.com" in their web browser, the DNS system looks up the associated CNAME record and then resolves it to the actual domain name or IP address where the website's content is hosted. This allows for flexibility in managing web services and content by pointing the "www" subdomain to a specific server or hosting provider.

It's important to note that while "www" is a common convention for web server subdomains, it's not mandatory. Websites can be configured to respond to requests for the root domain ("foobar.com") without requiring "www," or they can use other subdomains for different purposes. The choice of using "www" or not is largely a matter of preference and configuration by the website owner.

## Role of domain name:

The role of a domain name is fundamental in the functioning of the internet and web services. A domain name serves several important purposes:

1. **Human-Friendly Naming**: Domain names provide a human-readable and memorable way to access websites and services on the internet. Instead of having to remember numeric IP addresses (e.g., 192.168.0.1), users can simply type in a domain name (e.g., www.example.com) into their web browsers.

2. **Location Identifier**: Domain names serve as location identifiers for resources on the internet. They help users and computers locate and access websites, email servers, and other online services. When you enter a domain name in a web browser, the Domain Name System (DNS) translates it into the corresponding IP address, allowing your device to connect to the correct server.

3. **Branding and Identity**: Domain names are crucial for branding and establishing an online identity. They help businesses and individuals create a unique online presence, and the choice of a domain name can reflect the purpose, content, or identity of a website or online service.

4. **Email Addresses**: Domain names are also used to create custom email addresses. For example, if you own the domain "example.com," you can create email addresses like "yourname@example.com." Domain-based email addresses are commonly used for professional and personalized communication.

5. **Server and Service Organization**: Domain names allow organizations to organize their web servers and services under a unified naming structure. Subdomains, such as "blog.example.com" or "store.example.com," can be used to categorize and differentiate various services and web content.

6. **Global Accessibility**: Domain names are not restricted by geographical or network boundaries. They provide a globally accessible way to reach websites and services. This allows businesses and individuals to have a worldwide online presence.

7. **Ownership and Control**: Domain names represent ownership and control over a specific online resource. When you own a domain name, you have the authority to configure its DNS settings, direct traffic to different servers, and manage its associated services.

8. **Security**: Domain names can play a role in security, as they are often used to verify the authenticity of websites and protect against phishing attacks. SSL/TLS certificates are issued for domain names, assuring users that their connection to a website is encrypted and secure.

_In summary, domain names are essential in making the internet more accessible, user-friendly, and organized. They serve as the primary means of locating and identifying online resources, businesses, and individuals, and they play a crucial role in branding and establishing a digital presence._


## Protocol to communicate between the computer and the website

When a user requests a website, the communication between the user's computer and the web server is primarily facilitated through the use of the Hypertext Transfer Protocol (HTTP) over the Transmission Control Protocol (TCP) and Internet Protocol (IP). Here's how it works:

HTTP (Hypertext Transfer Protocol): HTTP is the protocol used for communication between a user's web browser (or client) and the web server. It defines how requests and responses should be formatted and transmitted. For secure communication, HTTPS (HTTP Secure) is used, which adds a layer of encryption using SSL/TLS protocols.

TCP (Transmission Control Protocol): HTTP operates on top of the TCP protocol. TCP is responsible for ensuring reliable, ordered, and error-checked delivery of data packets between the user's computer and the web server. It establishes a connection and manages the transfer of data.

IP (Internet Protocol): IP is used for routing and addressing the data packets between the user's computer and the web server. It determines how data is packetized and sent across the internet to reach its destination (the web server).

# 1. Distributed web infrastructure
![Distributed web infrastructure](https://github.com/GTDeschamps/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/1-distributed_web_infrastructure.png?raw=true)

##  what is a Load-Balancer

A load balancer is a critical component in network and server architecture that helps distribute incoming network traffic or requests across multiple servers or resources. The primary purpose of a load balancer is to optimize resource utilization, maximize throughput, minimize response time, and ensure high availability of services or applications.

There are two common load balancing setups: Active-Active and Active-Passive.

1. Active-Active Load Balancer:
- In an Active-Active setup, all the servers or resources are actively handling traffic simultaneously.
- Incoming requests are distributed evenly or according to a specified algorithm across all the available servers.
- This setup is typically used to balance the load across multiple servers, ensuring that all resources are utilized and providing redundancy in case one server fails.
- Active-Active configurations are often used for high-demand, highly available services like web applications, where multiple servers are needed to handle the traffic.

2. Active-Passive Load Balancer:
- In an Active-Passive setup, one server or resource (the "active" server) handles incoming traffic, while the other servers (the "passive" servers) remain on standby.
- The active server is the primary one that processes incoming requests, and the passive servers are only used when the active server fails or needs maintenance.
- This configuration is primarily used for failover and redundancy purposes, ensuring that the service remains available even if the primary server experiences issues.
- Active-Passive load balancing is often used for critical services where any downtime is unacceptable, like databases, where one server is processing transactions, and others are ready to take over in case of a failure.

Key Differences:
- Active-Active load balancing distributes traffic across multiple servers, all of which are actively handling requests, while Active-Passive load balancing uses one active server and others in standby.
- Active-Active setups are designed for load distribution and resource utilization, whereas Active-Passive setups are designed for redundancy and failover.
- Active-Active setups are suitable for applications with high traffic, where scaling resources is essential. Active-Passive setups are more about ensuring high availability.
- In Active-Active load balancing, all servers are continuously processing requests, which can be more resource-intensive compared to Active-Passive setups, where some servers remain idle until needed.
- Active-Active setups can handle more traffic but require careful configuration to ensure even distribution. Active-Passive setups are simpler to manage but don't utilize resources as efficiently.

The choice between these configurations depends on your specific needs, the nature of your services, and your tolerance for downtime or resource underutilization. Many organizations use a combination of both approaches to balance traffic and ensure high availability.

## what is a "MySQL master-Replica" cluster

A MySQL Master-Replica cluster, also known as a Master-Slave or Primary-Secondary cluster, is a common database architecture used to ensure high availability and data redundancy. In this setup, one MySQL server acts as the "master" or "primary," while one or more other MySQL servers act as "replicas" or "slaves." Replication is the process used to keep data synchronized between the master and the replicas.

Here's how MySQL Master-Replica replication works:

Master Server (Primary):

The master server is the primary database server that handles all write operations and changes to the database.
It contains the authoritative copy of the data.
Replica Servers (Secondary):

Replica servers are secondary database servers that replicate data from the master.
They serve read operations, which makes them suitable for handling read-heavy workloads.
Replicas are kept in sync with the master by copying the data and changes from the master server.
Replication Process:

When data is modified on the master server (e.g., an INSERT, UPDATE, DELETE operation), the master records the changes in its binary log (binlog).
The replicas continuously monitor the binlog on the master to identify changes.
Replicas apply the same changes to their own database copies, effectively mirroring the master's data.

# 2. Secured and monitored web infrastructure

![Secured and monitored web infrastructure](https://github.com/GTDeschamps/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/2-secured_and_monitored_web_infrastructure.png?raw=true)

## what is a Firewall (and his place in Web infrastructure)

A firewall is a network security device or software that acts as a barrier between a trusted network (like a company's internal network) and untrusted networks (such as the internet). Its primary purpose is to control the flow of network traffic and enforce security policies to protect the trusted network from unauthorized access, cyberattacks, and other potential threats.

Firewalls play a crucial role in web infrastructure by providing several key functions:

1. Packet Filtering: Firewalls examine packets of data as they travel between networks and make decisions based on predefined rules. They can allow or block traffic based on factors like source IP addresses, destination IP addresses, port numbers, and protocols.

2. Stateful Inspection: Modern firewalls often use stateful inspection to track the state of active connections. This allows them to make more intelligent decisions about allowing or denying traffic based on the context of the communication.

3. Proxy Services: Some firewalls can act as proxies, mediating communication between internal and external systems. They can cache web content, providing an additional layer of security and potentially improving performance.

4. Application Layer Filtering: Next-generation firewalls can inspect traffic at the application layer, making decisions based on the specific applications or services being accessed. This is especially useful for blocking threats and controlling access to specific web services.

5. Intrusion Detection and Prevention: Firewalls can incorporate intrusion detection and prevention systems (IDPS) to identify and block suspicious or malicious activities. This helps protect against attacks like malware, denial-of-service (DoS) attacks, and other security threats.

6. Virtual Private Network (VPN) Support: Many firewalls support VPNs, enabling secure communication over public networks. This is essential for remote access and connecting branch offices to the central network securely.

7. Logging and Reporting: Firewalls often maintain logs of network activities, which are critical for auditing and forensic analysis. They can generate reports to help network administrators understand the traffic patterns and potential security incidents.

In web infrastructure, firewalls are typically placed at various points to safeguard different layers of a network, including:

1. Perimeter Firewalls: These are positioned at the network's edge, between the internal network and the internet. They protect the entire network from external threats and unauthorized access.

2. Internal Firewalls: These are deployed within the internal network to segment it into separate security zones, ensuring that even if a threat breaches the perimeter, it cannot easily move laterally within the network.

3. Host-based Firewalls: These run on individual devices (e.g., servers or endpoints) and provide an additional layer of defense. They control traffic at the device level and can be used to enforce specific security policies.

4. Cloud Firewalls: In cloud-based web infrastructure, cloud providers often offer firewall services to control inbound and outbound traffic for virtual machines, containers, and other cloud resources.

Firewalls are a fundamental component of network security, and they help protect web infrastructure from a wide range of cyber threats, making them a critical element in maintaining the security and integrity of online services and data.

## What's the Monitoring

Monitoring in web infrastructure is the practice of systematically observing and collecting data about performance, availability, security, and resource utilization to ensure the web application functions optimally, stays available, and remains secure. It involves tracking metrics, generating alerts, and providing insights for proactive management and rapid issue response.

# 3. Scale up the infrastructure

![Scale up](https://github.com/GTDeschamps/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/3-scale_up.png?raw=true)

## conclusion: importance of redundancy

Redundancy in web infrastructure is crucial for ensuring high availability and fault tolerance. It involves duplicating critical components and data so that if one fails, another can seamlessly take over. This minimizes downtime, maintains reliability, and ensures uninterrupted service, which is essential for web applications and services to meet user expectations and business needs.

___________________________________________________________________________________
# Authors of project



Gael Deschamps 

From #C21 Holberton School Laval 
