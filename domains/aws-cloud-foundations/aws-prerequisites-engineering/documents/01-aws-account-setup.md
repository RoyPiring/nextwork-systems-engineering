# Set Up An AWS Account

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-account-setup)

## Business Context

### Problem Statement
Setting up an AWS account establishes a billing boundary and identity required to access AWS services. Credit card information is collected to enable billing alerts, fraud prevention, and account verification. No charges occur unless usage exceeds free tier limits or paid services are explicitly consumed.

### Use Cases
- Initial AWS account creation for learning and experimentation
- Establishing billing boundaries and cost controls
- Accessing AWS Free Tier services
- Setting up identity and access management foundation

### Prerequisites
- Valid email address
- Credit card for account verification (no charges unless usage exceeds free tier)
- Basic understanding of cloud computing concepts

### Scope
- AWS account creation and verification
- Free Tier access configuration
- Billing alert setup
- Basic security configuration

### Non-Goals
- Advanced IAM configuration (covered in Security & Compliance Engineering)
- Multi-account setup (beyond single account scope)
- Enterprise organization management

## Architecture

### Components
- **AWS Account:** Billing boundary and identity container
- **AWS Free Tier:** Time-bound and usage-bound service access
- **Billing Management:** Cost tracking and alerting
- **Identity Foundation:** Root account and initial access

### System Design
```
AWS Account
├── Billing Boundary
├── Free Tier Access
├── Service Access
└── Identity Foundation
```

### Integration Points
- AWS Console access
- Service API access
- Billing and cost management
- Free Tier service eligibility

## Implementation

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Getting Started with the AWS Free Tier

---

## Getting Started With AWS

Setting up the AWS account establishes a billing boundary and identity required to access AWS services. Credit card information is collected to enable billing alerts, fraud prevention, and account verification. No charges occur unless usage exceeds free tier limits or paid services are explicitly consumed.

The initial workload targets a static website hosted on Amazon S3. This establishes a minimal, low-risk environment to validate account access, basic storage configuration, and public content delivery without introducing compute or network complexity.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-account-setup_aa6d42ae)

---

## AWS Free Tier

The AWS Free Tier provides time-bound and usage-bound access to selected services to support evaluation and experimentation. Upon account creation, the environment includes promotional credits and access to services with defined free usage thresholds across compute, storage, database, and networking categories.

The Free Tier offering consists of promotional credits and a subset of services designated as always-free within specific limits. Credits expire after the defined period or once consumed. Usage outside these limits results in standard billing based on published AWS pricing.

After the Free Tier period ends, the account remains active and retains all configured resources and data. Services that exceed free thresholds or are no longer covered incur charges. Ongoing cost control requires monitoring usage, understanding service limits, and tracking expiration dates within a personal or organizational financial process.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-account-setup_ba6d42ae)

---

## Excited to share my progress! Let's connect.

### To learn with other AWS students and get support, I'm joining the NextWork community.

---

## Validation

### Expected Results
- AWS account created and verified
- Free Tier access enabled
- Billing alerts configured
- Account accessible via AWS Console
- Initial workload (S3 static website) can be deployed

### Verification Steps
1. **Account Creation:** Confirm account creation
   - Access AWS Console successfully
   - Verify account ID and email confirmation
2. **Free Tier Access:** Verify Free Tier eligibility
   - Check Free Tier dashboard
   - Confirm service availability
3. **Billing Setup:** Verify billing configuration
   - Billing alerts configured
   - Payment method verified
4. **Service Access:** Test basic service access
   - Create S3 bucket (Free Tier eligible)
   - Verify no charges for Free Tier usage

### Observed Results
TODO: capture account creation confirmation, Free Tier access verification, and initial service access test results

### Known Failure Conditions
- **Account Verification Failure:** Email verification required, check spam folder
- **Payment Method Rejection:** Contact AWS support or use alternative payment method
- **Free Tier Not Available:** Verify account age and region selection

---

## Navigation

| Next |
|------|
| [AWS Beginners Challenge](./aws-beginners-challenge.md) |