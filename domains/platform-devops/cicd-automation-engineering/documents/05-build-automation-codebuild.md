<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Continuous Integration with CodeBuild

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-codebuild-updated)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Canonical  
**Audience:** Builder | Designer | Learner  
**Production Use:** Yes  
**System Dependency:** Required

**Prerequisites:**
- AWS account with CodeBuild access
- Source code repository configured
- Understanding of build processes
- Knowledge of build specifications (buildspec.yml)
- Basic familiarity with build artifacts
- Understanding of IAM roles for CodeBuild

**Outputs:**
- CodeBuild project configuration
- Build specification files
- Build artifacts
- Build validation results
- Automated build test evidence

---

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_35588a47)

---

## Introducing Today's Project!

This project implements a basic continuous integration workflow using AWS CodeBuild triggered by source changes in a GitHub repository. The system exists to validate that code changes can be automatically built and packaged without manual intervention, establishing a repeatable CI baseline suitable for extension into a full pipeline.

### Key tools and concepts

The implementation relies on AWS CodeBuild for managed builds, Amazon S3 for artifact storage, AWS IAM for execution permissions, and GitHub as the source control system. These components collectively support CI/CD patterns by separating source, build execution, identity, and artifact persistence.

### Project reflection

The build was completed within a short execution window and surfaced IAM permission gaps as the primary constraint. Resolving service role access clarified the dependency between CodeBuild execution and downstream services. The outcome demonstrates a functional, event-driven build triggered by repository changes and producing verifiable outputs.

This project establishes the CI layer of a broader pipeline and is intentionally limited to build and packaging concerns. It assumes prior completion of foundational source control and IAM setup and is designed to be extended in subsequent stages.

---

## Setting up a CodeBuild Project

AWS CodeBuild provides a managed build service that executes build instructions in an isolated environment in response to source changes. Its role in this system is to standardize build execution, reduce manual variability, and provide fast feedback on code changes.

The project configures GitHub as the source provider so that commits automatically initiate builds. Selecting GitHub as the source establishes a direct integration path and enables event-based triggers rather than manual build initiation.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_fewgrhte)

---

## Connecting CodeBuild with GitHub

GitHub Apps are used to authenticate CodeBuild to the repository with scoped, non-user credentials. This approach reduces long-lived credential risk and limits access to only the permissions required for CI operations.

The integration allows CodeBuild to receive source events and retrieve code automatically, forming the control plane link between version control and the build service.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_a7c98e2d)

---

## CodeBuild Configurations

### Environment

The environment configuration defines how builds execute, including compute capacity, operating system image, environment variables, IAM service role, and execution timeout. These settings constrain resource usage, control permissions, and ensure builds run in a predictable and repeatable context.

### Artifacts

Build artifacts represent the outputs of the build process. In this implementation, the build produces application files and a JSON report that are stored in an Amazon S3 bucket to provide durable, externally accessible build results.

### Packaging

Artifacts are packaged and uploaded to S3 to decouple build execution from downstream consumption. This enables other services or pipeline stages to retrieve immutable build outputs without direct dependency on the build environment.

### Monitoring

Amazon CloudWatch Logs are enabled to capture build output and execution status. Log visibility supports failure analysis, performance inspection, and validation that build steps executed as intended.

---

## buildspec.yml

The initial build failed because the repository did not include a buildspec.yml file, which CodeBuild requires to define build behavior. This file serves as the authoritative specification for build phases, commands, and artifact handling.

The build specification defines ordered phases including install, pre-build, build, and post-build. Each phase scopes responsibility for environment setup, preparation, compilation or packaging, and post-processing actions such as test execution or artifact publication.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_35588a47)

---

## Success!

A subsequent build failed due to insufficient permissions on the CodeBuild service role to access AWS CodeArtifact. This highlighted the separation between build execution and dependency retrieval permissions.

Updating the IAM role to allow read access to the required CodeArtifact repository resolved the failure.

After the policy change, the build completed successfully, logs showed no errors, and the presence of artifacts in S3 confirmed correct packaging.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_d9cc6191)

---

## Automating Testing

The build process was extended to include automated test execution covering authentication edge cases. The intent is to detect regressions and basic security failures during the CI phase rather than after deployment.

Test execution was integrated by updating buildspec.yml to invoke a test script during the build.

Committing these changes to GitHub triggered a new build, which executed the tests successfully and validated the CI systemΓÇÖs ability to enforce automated checks.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-codebuild-updated_sm-test-script-upload)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [Infrastructure CloudFormation](./04-infrastructure-cloudformation.md) | [Package Management CodeArtifact](./06-package-management-codeartifact.md) |