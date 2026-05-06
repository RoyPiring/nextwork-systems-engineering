<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-peering)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Reference  
**Audience:** Builder | Designer | Learner  
**Production Use:** Conditional  
**System Dependency:** Optional

**Prerequisites:**
- Multiple VPCs configured
- Understanding of VPC peering concepts
- Knowledge of non-overlapping CIDR blocks
- Understanding of route table configuration
- Basic knowledge of transitive vs. non-transitive routing
- Access to configure peering connections

**Outputs:**
- VPC peering connection configuration
- Route table updates for peering
- Cross-VPC connectivity validation
- Peering connection test results
- Multi-VPC architecture documentation

---

## VPC Peering

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC provides an isolated, software-defined network boundary within an AWS account. It controls IP addressing, routing, and traffic flow to enforce security isolation, enable deterministic network design, and support scalable workload placement across subnets and availability zones. VPCs exist to give operators explicit control over network topology rather than relying on provider-managed defaults.

### How I used Amazon VPC in this project

This project uses Amazon VPC to establish controlled connectivity between two independent network domains using VPC peering. The intent is to enable private IP communication while preserving administrative separation, avoiding shared routing tables or transitive network assumptions.

### One thing I didn't expect in this project was...

Route table configuration proved to be the primary constraint. CIDR planning and explicit route propagation are required for deterministic traffic flow. Misalignment at this layer results in silent traffic drops, not explicit failures, which makes validation essential.

### This project took me...

The implementation was completed in approximately 60 minutes. Scope was intentionally limited to core networking primitives: VPCs, routing, peering, and EC2-based validation. The objective was functional correctness, not production hardening.

---

## In the first part of my project...

### Step 1 - Set up my VPC

Two separate VPCs were created to establish independent routing domains. This isolates address space, enforces explicit connectivity decisions, and provides a clear baseline for validating peering behavior. The VPC resource map was used to confirm structural correctness.

### Step 2 - Create a Peering Connection

A VPC peering connection was established to allow private IP communication between the two VPCs. Peering was selected to provide low-latency, non-transitive connectivity without introducing centralized routing or gateway dependencies.

### Step 3 - Update Route Tables

Each VPC route table was explicitly updated to direct traffic destined for the peer CIDR block to the peering connection. This step is required because VPC peering does not modify routing automatically. Correct routing is the gating factor for any cross-VPC traffic.

### Step 4 - Launch EC2 Instances

EC2 instances were launched in each VPC to act as network endpoints. These instances provide concrete verification of routing, security group behavior, and peering functionality rather than relying on control-plane status alone.

---

## Multi-VPC Architecture

Two VPCs were deployed to model a multi-network environment where connectivity is intentional rather than implicit. This mirrors common enterprise patterns where workloads are segmented by environment, trust boundary, or ownership.

VPC CIDR blocks were intentionally non-overlapping. Overlapping CIDRs are not supported by VPC peering and would result in ambiguous routing decisions and undefined traffic behavior.

### I also launched 2 EC2 instances

Two EC2 instances were launched as test endpoints. EC2 Instance Connect was used to manage SSH access without distributing long-lived key pairs, reducing access surface area during validation.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_11111111)

---

## VPC Peering

VPC peering provides direct, private connectivity between two VPCs within the same region. It simplifies network topology while maintaining isolation at the account and routing level. Peering does not support transitive routing and must be designed accordingly.

The peering connection enables workloads in separate VPCs to communicate using private IPs as if they were on a shared network, without merging security boundaries or routing tables.

The requester-accepter model enforces mutual authorization. One VPC initiates the request, and the peer explicitly accepts it, preventing unintended connectivity and preserving administrative control.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

Route tables were updated after peering acceptance to enable traffic flow between CIDR ranges. Each route explicitly targets the peering connection to ensure deterministic forwarding.

Each VPC route table includes a destination matching the peer VPC CIDR with the peering connection as the target. Without this configuration, traffic would never leave the source VPC.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_4a9e8014)

---

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

EC2 Instance Connect was used to establish administrative access for validation and troubleshooting. This method relies on IAM-based authorization and avoids persistent SSH key distribution.

### Step 6 - Connect to EC2 Instance 1

Access to the first instance was used to identify and correct configuration issues impacting connectivity. The focus was on validating network reachability rather than application behavior.

### Step 7 - Test VPC Peering

Network tests were executed from Instance 1 to Instance 2 to confirm bidirectional communication. Successful traffic flow indicates correct routing, security group rules, and peering state.

---

## Troubleshooting Instance Connect

EC2 Instance Connect provided secure shell access without relying on public key distribution. This enabled direct inspection of network behavior and instance-level configuration.

Initial access failed due to restrictive security group rules. SSH ingress on port 22 was not permitted, preventing Instance Connect from establishing a session.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

Elastic IPs were used to provide stable public addressing during troubleshooting. This allowed consistent access for validation when dynamic public IP assignment introduced ambiguity.

Associating an Elastic IP restored external reachability, enabling direct testing and configuration correction.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

ICMP echo requests were used to validate basic network connectivity between instances across VPCs. This test confirms routing, peering functionality, and firewall behavior.

Successful responses indicate functional private connectivity, correct route table configuration, and permissive ICMP rules.

Security groups were updated to allow inbound SSH traffic from the peer VPC CIDR, enabling controlled administrative access while maintaining network isolation.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-peering_7a29d352)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [EC2 Networking](./07-ec2-networking.md) | [CloudFront Integration](./09-cloudfront-integration.md) |