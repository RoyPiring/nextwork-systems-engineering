<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Packages with CodeArtifact

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codeartifact-updated)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Canonical  
**Audience:** Builder | Designer | Learner  
**Production Use:** Yes  
**System Dependency:** Required

**Prerequisites:**
- AWS account with CodeArtifact access
- Understanding of package management concepts
- Knowledge of dependency management
- Basic familiarity with artifact repositories
- Understanding of IAM policies for CodeArtifact
- Access to configure package repositories

**Outputs:**
- CodeArtifact repository configuration
- Package versioning and storage
- Repository access policies
- Package management validation results
- Artifact repository integration evidence

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Introducing Today's Project!

This project implements AWS CodeArtifact as a centralized dependency repository for a Java web application running on Amazon EC2. The objective is to control how dependencies are retrieved, cached, and authenticated, establishing a secure and repeatable dependency management layer that integrates cleanly into a CI/CD pipeline.

Project Steps:

PART 1: Web App Setup

Step #1: Launch an EC2 instance.

Step #2: Prepare the instance with Java, Maven, and source code required to validate dependency resolution through CodeArtifact.

### Key tools and concepts

Services used include AWS CodeArtifact and AWS IAM, with EC2 acting as the execution environment. The core concepts exercised were private artifact repositories, upstream dependency resolution, token-based authentication, and IAM role-based access control.

CodeArtifact: Centralized storage and caching for Java dependencies.

CI/CD: Dependency governance as a prerequisite for reliable builds.

Amazon EC2: Compute environment for building and validating artifacts.

AWS IAM: Permission boundaries and identity-based access to repositories.

GitHub: Source control feeding downstream build systems.

### Project reflection

This project took approximately one hour. The primary complexity was aligning IAM policies, roles, and instance profiles so Maven could authenticate to CodeArtifact without static credentials. The most valuable outcome was observing dependency resolution flow end to end, from Maven to CodeArtifact and upstream to Maven Central.

This work establishes the dependency management layer required for a production-grade CI/CD pipeline. Securing and centralizing dependencies reduces supply chain risk and ensures builds are deterministic across environments.

---

## CodeArtifact Repository

AWS CodeArtifact is used to store, cache, and serve software packages required by the application. It provides a controlled repository boundary that decouples builds from direct reliance on public package sources.

The CodeArtifact domain groups related repositories under a shared security and permission model. This allows consistent access controls to be applied across multiple repositories without duplicating IAM configuration.

The repository is configured with Maven Central as an upstream source. When a dependency is not present locally, CodeArtifact retrieves it from the upstream repository, caches it, and serves it to future builds.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_n4o5p6q7)

---

## CodeArtifact Security

### Issue

Initial attempts to authenticate Maven against CodeArtifact failed due to missing credentials. The EC2 instance did not have an identity authorized to request CodeArtifact tokens, which prevented dependency resolution.

### Resolution

An IAM policy granting CodeArtifact read and token permissions was created and attached to an IAM role. That role was then associated with the EC2 instance, allowing the instance to obtain temporary credentials automatically.

IAM roles were used instead of static credentials to enforce least privilege, enable automatic credential rotation, and avoid embedding secrets in configuration files. This approach aligns with AWS security best practices for service-to-service access.

---

## The JSON policy attached to my role

The JSON policy attached to the role defines explicit permissions for retrieving authorization tokens, resolving repository endpoints, and reading artifacts. Permissions are scoped to CodeArtifact operations and rely on AWS STS for temporary access

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_23rp7q8r9)

---

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures repository endpoints, authentication tokens, and profiles without modifying the applicationΓÇÖs pom.xml. This separation keeps build logic independent from environment-specific credentials.

Maven orchestrates dependency resolution, compilation, and packaging. During compilation, Maven retrieves dependencies through CodeArtifact, ensuring all artifacts are sourced from a controlled repository rather than directly from public endpoints.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_c17eace8)

---

## Verify Connection

The CodeArtifact repository shows Java dependencies cached as a result of the Maven build. These artifacts represent the transitive dependencies declared in the projectΓÇÖs pom.xml and confirm successful upstream resolution and local storage.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_1d79e699)

---

## Uploading My Own Packages

A custom package was created, published to CodeArtifact, retrieved, and verified. This exercise demonstrates the full artifact lifecycle: creation, integrity validation, publication, storage, and consumption.

A SHA-256 hash was generated for the package prior to upload to ensure integrity during transfer and storage. CodeArtifact validated the hash on ingestion to confirm the asset was not altered.

The AWS CLI was used to publish the package with explicit metadata including domain, repository, namespace, format, and version. Successful publication was confirmed by inspecting the package metadata and version history in the CodeArtifact console.

The package was then downloaded from CodeArtifact and inspected locally, completing the producer-to-consumer workflow used by internal engineering teams to distribute proprietary libraries.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codeartifact-updated_sm12-upload)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [Build Automation CodeBuild](./05-build-automation-codebuild.md) | [Idempotent Provisioning](./07-idempotent-provisioning.md) |