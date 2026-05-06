<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Website Delivery with CloudFront

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-cloudfront)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Reference  
**Audience:** Builder | Designer | Learner  
**Production Use:** Conditional  
**System Dependency:** Optional

**Prerequisites:**
- VPC and application resources configured
- Understanding of CDN concepts
- Knowledge of CloudFront distribution patterns
- Understanding of origin configuration
- Basic familiarity with content delivery networks
- Access to configure CloudFront distributions

**Outputs:**
- CloudFront distribution configuration
- Origin configuration with VPC resources
- CDN performance validation results
- Content delivery test evidence
- CloudFront integration documentation

---

## Website Delivery with CloudFront

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_1dddddwe)

---

## Introducing Today's Project!

This project demonstrates the use of Amazon CloudFront to deliver static web content with lower latency by caching objects at edge locations closer to end users. The system is designed to illustrate how a CDN sits in front of an origin to improve response times, reduce origin load, and standardize content delivery behavior.

### Tools and concepts

The implementation uses Amazon S3 as the origin for static assets and Amazon CloudFront as the content delivery layer. Core concepts exercised include CDN behavior, origins, distributions, caching mechanics, and S3 bucket policies that control access between CloudFront and the origin.

### Project reflection

The project scope focused on validating baseline CloudFront behavior rather than production-scale optimization.

The primary complexity involved aligning S3 access controls with CloudFront access requirements to avoid unintended public exposure while maintaining functional content delivery.

---

## Set Up S3 and Website Files

An Amazon S3 bucket was provisioned to store static website assets including HTML, CSS, JavaScript, and images. S3 serves as the system of record for content, while CloudFront is introduced later as a delivery layer rather than a storage mechanism.

The website consists of a basic HTML entry point, a stylesheet defining presentation, and a client-side script enabling interactivity. These files represent a minimal static workload suitable for CDN caching and edge distribution.

The uploaded assets were validated by direct access through the S3 object URLs to confirm correct storage, rendering, and client-side execution prior to introducing CloudFront. This establishes a known-good origin state before layering additional infrastructure.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_qgo7wcd3)

---

## Exploring Amazon CloudFront

Amazon CloudFront functions as a globally distributed CDN that caches content at edge locations to reduce latency for geographically dispersed users. The system improves perceived performance by serving requests from the nearest available edge rather than the origin region.

CloudFront distributions define how content is cached, requested, and served. In this project, a distribution was configured with the S3 bucket as its origin, establishing CloudFront as the sole public-facing endpoint for content delivery.

The default root object was set to index.html to ensure consistent behavior when users access the distribution domain without specifying a file path. This configuration aligns CloudFront request handling with standard static website entry patterns.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_qgo7wcdt)

---

## Handling Access Issues

Initial access failures occurred due to restrictive S3 permissions that prevented CloudFront from retrieving objects. This highlighted the dependency between origin access configuration and successful CDN operation.

Resolution required validating object-level permissions, bucket policy configuration, and CloudFront origin settings to ensure CloudFront could read content while avoiding unrestricted public access.

The issue exposed the difference between public S3 access and controlled access via CloudFront. Without explicit authorization, CloudFront cannot fetch objects from a private bucket, resulting in access denied errors.

Origin Access Control (OAC) was identified as the mechanism that allows CloudFront to securely access a private S3 bucket using a managed identity rather than public permissions.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_egrhntyu)

---

## Updating S3 Permissions

Origin Access Control restricts S3 access exclusively to the associated CloudFront distribution, while the bucket policy defines the enforcement point for that restriction. Together, they form the access boundary between the CDN and the origin.

Updating the bucket policy to trust the CloudFront OAC allows CloudFront to retrieve objects without exposing the bucket publicly. This configuration supports secure content delivery and prevents direct access paths that bypass the CDN.

The resulting design limits S3 access to authorized CloudFront requests only, reducing the attack surface and aligning with least-privilege access principles.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_eg98ntyu)

---

## S3 vs CloudFront for Hosting

Direct S3 static website hosting requires public read permissions, which introduces broader access than necessary for most internet-facing workloads. In this project, private bucket settings initially caused 403 errors due to missing public authorization.

aking objects publicly readable resolved the S3-only hosting issue by explicitly granting anonymous access through the bucket policy. This approach enables functionality but weakens access control boundari

In contrast, CloudFront with Origin Access Control maintains a private S3 bucket while still enabling global access through the CDN. 

This model provides stronger security guarantees and more granular control over how content is exposed.

---

## S3 vs CloudFront Load Times

Page load time reflects the end-to-end latency experienced by a user requesting content. CloudFront reduces this latency by serving cached content from edge locations closer to users instead of a single regional endpoint.

Deployments. S3-only hosting is better suited for low-traffic, region-specific use cases where simplicity and minimal configuration outweigh performance and security requirements.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-networks-cloudfront_12verpuh)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [VPC Peering Advanced](./08-vpc-peering-advanced.md) | [Isolated Network Test](./10-isolated-network-test.md) |