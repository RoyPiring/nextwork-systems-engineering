<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-secretsmanager)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Canonical  
**Audience:** Builder | Designer | Learner  
**Production Use:** Yes  
**System Dependency:** Required

**Prerequisites:**
- AWS account with Secrets Manager access
- GitHub account and repository access
- Application codebase for integration
- Understanding of secret management concepts
- AWS SDK or CLI installed
- Basic knowledge of application configuration patterns

**Outputs:**
- Secrets Manager secret configuration
- Application code updated for secret retrieval
- GitHub repository with secrets removed
- Secret access validation results
- IAM policies for secret access

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

### Project overview

This project demonstrates the security implications of embedding cloud credentials in application code and the corrective use of AWS Secrets Manager to externalize and control sensitive configuration. The system transitions a web application from static credential storage to managed secret retrieval to reduce exposure risk and align with standard cloud security practices. The workflow validates how secrets are removed from source control, stored centrally, and accessed programmatically at runtime without embedding sensitive values in code.

### Tools and concepts

The system uses AWS Secrets Manager as the authoritative store for sensitive credentials, with AWS IAM enforcing access boundaries. GitHub functions as the version control system where exposure risk is evaluated. The project centers on hardcoded credential risks, secret lifecycle management, and controlled retrieval patterns rather than tool usage alone.

### Project reflection

The implementation highlights the operational friction introduced when retrofitting secret management into existing code. The primary constraint addressed is maintaining application functionality while removing embedded credentials. 

The outcome demonstrates reduced credential exposure and clearer separation between code and configuration.

---

## Hardcoding credentials

The initial state of the system embeds AWS access keys directly in application code, creating a direct attack surface if the repository is shared or compromised. This approach violates basic security and compliance expectations by storing secrets in plaintext, coupling credentials to version control history, and enabling full account compromise if leaked. 

The example credentials are intentionally non-production and exist only to illustrate the failure mode.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

A separate execution path uses real AWS credentials to validate authentication behavior. 

Environment configuration differences exposed authentication failures when sample credentials were replaced.

Updating environment variables corrected the mismatch and restored access, demonstrating that credential validity and scope directly affect application authentication without changing application logic.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

The repository is forked to isolate changes from the upstream source while preserving commit history.

When insecure code containing credentials is pushed, GitHub blocks the operation through automated secret scanning.

This control prevents accidental credential disclosure and reinforces the requirement to externalize secrets before publishing code.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

AWS Secrets Manager provides centralized storage and controlled access for sensitive values such as access keys, database credentials, and API tokens.

. The service supports automated rotation to reduce credential lifetime and limit blast radius after compromise.

Language-specific SDK examples reduce integration variance and standardize secure retrieval patterns across applications.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

Application configuration is modified to resolve credentials at runtime through AWS Secrets Manager rather than static values.

The configuration layer retrieves the secret payload and extracts required fields for authentication. This design decouples sensitive data from the codebase, enabling credential updates without code changes and reducing exposure in source control.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

Repository history is rebased to produce a linear commit sequence that removes insecure commits from the visible history.

Conflict resolution ensures the final state reflects Secrets Manager–based authentication.

Post-rebase validation confirms successful AWS access using managed secrets by verifying connectivity, data access, and resource authorization without authentication errors.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [IAM Least Privilege](./01-iam-least-privilege.md) | [Boundary Enforcement](./03-boundary-enforcement.md) |