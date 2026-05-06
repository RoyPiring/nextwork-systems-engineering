<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Canonical  
**Audience:** Builder | Designer | Learner  
**Production Use:** Yes  
**System Dependency:** Required

**Prerequisites:**
- VPC and subnets configured
- Understanding of firewall concepts
- Knowledge of stateful vs. stateless firewalls
- Understanding of security group rules
- Basic knowledge of network ACLs

**Outputs:**
- Security group configurations
- Network ACL configurations
- Security rule validation results
- Traffic flow test evidence
- Defense-in-depth validation

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

This project examines how traffic moves within an Amazon VPC and how that traffic is controlled using native AWS networking and security primitives. The focus is on understanding enforcement points and failure boundaries rather than on procedural setup.

Amazon VPC is a logically isolated virtual network within an AWS account that defines IP addressing, routing, and network-level security boundaries. It exists to provide deterministic control over network topology, traffic flow, and isolation between workloads.

### How I used Amazon VPC in this project

The VPC was configured to control traffic flow using route tables, security groups, and network ACLs. Each control plane component was used for its intended scope, instance-level or subnet-level, to demonstrate layered network security and predictable traffic behavior.

### One thing I didn't expect in this project was...

The project exposed how easily misaligned security group and network ACL rules can create unintended access paths or silent traffic drops. It reinforced the need to design security controls with explicit intent rather than relying on defaults.

### This project took me...

The implementation was completed within a short time window, with scope limited to validating traffic flow and security behavior. The constrained duration reflects the focused nature of the configuration rather than production-scale complexity.

---

## Route tables

Route tables define how traffic is forwarded from subnets by mapping destination CIDR ranges to targets such as internet gateways or local routing. They exist to make traffic paths explicit and to prevent unintended egress or ingress.

Route tables direct subnet traffic to the internet gateway, enabling communication outside the VPC. Without an explicit route, subnet resources remain isolated by design, even if other security controls allow the traffic.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Each route consists of a destination CIDR block and a target that determines where matching traffic is sent. This mechanism enables controlled routing to the internet, AWS-managed services, or private networks.

This route explicitly allows outbound traffic to any IPv4 address via the internet gateway and is required for public subnet connectivity.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups act as stateful, instance-level firewalls that define allowed inbound and outbound traffic based on protocol, port, and source or destination. They exist to enforce least-privilege access directly at the workload boundary.

### Inbound vs Outbound rules

Inbound rules define which external sources can initiate connections to an instance. In this project, inbound SSH access was restricted to a specific source address to limit administrative exposure.

Outbound rules define which destinations an instance can reach. By default, all outbound traffic is allowed, which simplifies connectivity but must be constrained in higher-security environments.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are stateless, subnet-level access controls that evaluate traffic before it reaches individual resources. They exist to provide a coarse-grained enforcement layer that applies uniformly to all resources within a subnet.

### Security groups vs. network ACLs

Security groups apply at the instance level and track connection state. Network ACLs apply at the subnet level and require explicit allow rules for both inbound and outbound traffic.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

Network ACLs evaluate inbound and outbound rules independently. Default network ACLs allow all traffic, which reduces friction but offers minimal protection.

Custom network ACLs deny all traffic by default, requiring explicit rule definition. This model reduces accidental exposure by forcing intentional access design.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

Multiple VPCs were created to observe how resources are organized and tracked across availability zones. The exercise highlights how regional and zonal boundaries affect visibility and operational management.

EC2 Global View provides a consolidated view of instances across regions and accounts, reducing manual inspection overhead. It exists to support operational awareness in environments with distributed resources.

Visualize and manage EC2 instances across regions for efficient resource allocation, monitoring, and troubleshooting. This capability supports cost control, security review, and operational diagnostics in multi-region deployments.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-security_b03ea6162)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [Routing Boundaries](./03-routing-boundaries.md) | [VPC Endpoints](./05-vpc-endpoints.md) |