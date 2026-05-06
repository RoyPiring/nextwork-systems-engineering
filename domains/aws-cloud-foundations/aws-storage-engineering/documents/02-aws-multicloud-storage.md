# Multi-Cloud Data Transfer with AWS and GCP

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-multicloud-storage)

## Business Context

### Problem Statement
This project implements a controlled data transfer path between Amazon S3 and Google Cloud Storage using Google Cloud Storage Transfer Service. The system demonstrates cross-cloud object movement without duplicating credentials or building custom transfer logic. The primary objective is to validate interoperability between AWS and GCP storage services using native, managed transfer capabilities.

### Use Cases
- Cross-cloud data migration
- Multi-cloud backup strategies
- Compliance-driven data placement
- Cloud provider interoperability validation

### Prerequisites
- AWS account with S3 access
- Google Cloud Platform account
- IAM role configuration knowledge
- Understanding of identity federation

### Scope
- S3 bucket as source
- GCP Cloud Storage as destination
- Storage Transfer Service configuration
- Identity federation setup
- Transfer job execution

### Non-Goals
- Production-scale optimization
- Advanced transfer scheduling
- Multi-region replication
- Custom transfer tooling

## Architecture

### Components
- **Amazon S3:** Source object store
- **Google Cloud Storage:** Destination object store
- **Storage Transfer Service:** Managed transfer orchestration
- **AWS IAM Role:** Federated identity for cross-cloud access
- **Amazon SQS:** Transfer state coordination

### System Design
```
S3 Bucket (Source)
    ↓
IAM Role (Federation)
    ↓
Storage Transfer Service
    ↓
GCS Bucket (Destination)
```

### Integration Points
- S3 bucket access via IAM role
- GCP Storage Transfer Service
- Identity federation trust relationship
- SQS for transfer coordination

## Implementation

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s5k4l5m6)

---

## Introducing Today's Project!

This project implements a controlled data transfer path between Amazon S3 and Google Cloud Storage using Google Cloud Storage Transfer Service. The system demonstrates cross-cloud object movement without duplicating credentials or building custom transfer logic. The primary objective is to validate interoperability between AWS and GCP storage services using native, managed transfer capabilities.

### Tools and concepts

The system uses Google Cloud Storage Transfer Service to orchestrate data movement, Amazon S3 as the source object store, and Google Cloud Storage as the destination. Identity and access control is enforced through AWS IAM roles and GCP service identities. Amazon SQS is used by the transfer service to track and coordinate object transfer state.

### Project reflection

The implementation focuses on correctness of identity federation and transfer execution rather than throughput optimization or production scale. The critical engineering constraint is the trust relationship configuration that allows GCP to assume a limited AWS IAM role for read access to S3 objects. Successful transfer confirms that the trust boundary and permissions model function as designed.

---

## Setting up Data in S3

An Amazon S3 bucket is used as the authoritative source for objects being transferred. A test object is placed in the bucket to validate permissions, object visibility, and transfer behavior. This step establishes a known data set and isolates transfer issues from data availability or bucket misconfiguration.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s1g7h8j9)

---

## Setting up GCP

A Google Cloud project is configured to host the destination Cloud Storage bucket and to run Storage Transfer Service jobs. Cloud Storage is used strictly as the destination object store for this workflow.

Account setup and service enablement ensure that required APIs, service identities, and permissions are available before initiating any cross-cloud access.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s2g8h9j0)

---

## Storage Transfer

The system uses Storage Transfer Service to automate object movement between cloud providers. This service addresses common requirements such as data migration, backup replication, and compliance-driven data placement without custom tooling. Using managed transfers reduces operational risk by delegating retry logic, integrity checks, and scheduling to the platform.

Both one-time and recurring transfer modes are supported. One-time transfers are used for initial migration or validation.

Recurring transfers support periodic synchronization patterns where source data changes over time. The selection of transfer type defines scheduling behavior but does not change the underlying trust or access model.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s3k2l3m4)

---

## Granting GCP Access to AWS

Cross-cloud access is established using identity federation rather than static credentials. GCP assumes an AWS IAM role that grants scoped read access to the S3 bucket. This approach centralizes authentication, limits credential exposure, and enforces least privilege across cloud boundaries.

A custom AWS IAM role is created because managed policies do not address this specific federation pattern. The role includes a trust policy that explicitly allows the GCP service identity to assume it.

The trust policy uses a subject identifier to restrict which GCP entities are authorized, preventing unintended cross-account access.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s4k3l4m5)

---

## Transferring from S3 to GCS!

The destination Cloud Storage bucket is configured with an explicit region and storage class to control latency, cost, and compliance characteristics. These settings define how and where data is stored after transfer, independent of the source environment.

Validation follows the same process as non-manifest transfers, with emphasis on object count and metadata consistency. The manifest provides an additional control surface for auditing and repeatability without altering the underlying transfer mechanism.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_s5k4l5m6)

---

## Transfer with a Manifest

A manifest file is used to define an explicit inventory of objects to be transferred. The manifest specifies object names and attributes, allowing the transfer service to validate completeness and detect discrepancies. This approach is critical for large or regulated data sets where implicit bucket-wide transfers are not acceptable.

Validation follows the same process as non-manifest transfers, with emphasis on object count and metadata consistency. The manifest provides an additional control surface for auditing and repeatability without altering the underlying transfer mechanism.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-multicloud-storage_rththrthrth)

---

## Trial, Error, Success

---

## Validation

### Expected Results
- S3 bucket configured with test data
- GCP project and Cloud Storage bucket created
- IAM role with trust policy configured
- Storage Transfer Service job created
- Objects transferred successfully
- Transfer validation completed

### Verification Steps
1. **S3 Setup:** Verify source bucket and objects
   - Check test objects in S3
   - Verify bucket permissions
2. **GCP Setup:** Verify destination configuration
   - Check Cloud Storage bucket created
   - Verify project and API access
3. **Identity Federation:** Verify IAM role configuration
   - Check trust policy for GCP service identity
   - Verify role permissions for S3 read access
4. **Transfer Job:** Verify job creation and execution
   - Check transfer job status
   - Verify job configuration
5. **Transfer Validation:** Verify objects transferred
   - Compare source and destination object counts
   - Verify object integrity
6. **Manifest Transfer:** Test manifest-based transfer
   - Create manifest file
   - Verify manifest transfer execution

### Observed Results
TODO: capture S3 bucket configuration, GCP setup confirmation, IAM role trust policy, transfer job execution results, object transfer validation, and manifest transfer test results

### Known Failure Conditions
- **IAM Trust Policy Errors:** Incorrect service identity, verify GCP service account
- **S3 Access Denied:** IAM role permissions insufficient, verify role policy
- **Transfer Job Failures:** Check job status and error messages
- **Object Count Mismatch:** Verify source objects and transfer configuration
- **Manifest Format Errors:** Verify manifest file format and syntax

---

## Navigation

| Previous |
|----------|
| [AWS Host a Website on S3](./aws-host-a-website-on-s3.md) |