# Managed Services:
This is a collection of AWS infra, what it facilitates.

## Table of Contents

| Topic                                  | Image                    |
|----------------------------------------|--------------------------|
| AWS Internet Gateway & NAT Gateway     |  <img width="665" alt="Screenshot 2023-08-20 at 12 30 17 PM" src="https://github.com/ishan-backend/aws/assets/88132188/fbbc695d-961a-4f39-bec0-4413d4045892">  |
```
1. Internet Gateway (IGW):
   - Purpose: Enables instances in a public subnet to initiate requests to the public internet.
   - Functionality:
     - Allows outbound requests to the internet from public-facing instances.
     - Permits inbound requests from the internet to reach instances using their public IP addresses.
   - Use Cases:
     - Ideal for public-facing instances like Load Balancer servers (e.g., NginX) and API/Frontend servers.
   - Cost:
     - You're only charged for data transfer; no charges for the gateway itself.

2. Network Address Translation Gateway (NAT GW):
   - Purpose: Empowers instances in a private subnet to initiate requests to the public internet.
   - Functionality:
     - Allows outbound requests to the internet from private instances.
     - Does not allow inbound requests from the internet to reach instances, enhancing security.
   - Use Cases:
     - Suited for private instances like Database machines and internal application servers.
   - Security:
     - Enhances security by hiding servers from the external world.
   - Cost:
     - In addition to data transfer costs, AWS charges per hour for each provisioned NAT GW.

Both IGW and NAT GW are crucial for managing traffic flow in your AWS infrastructure. They are attached to Subnets using Route tables to control the flow of traffic effectively.
```

