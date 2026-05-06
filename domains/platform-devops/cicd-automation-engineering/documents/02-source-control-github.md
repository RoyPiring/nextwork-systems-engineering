<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a GitHub Repo with AWS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-github)

**Author:** Roy Piring Jr  
**Email:** rpiringhawaii@gmail.com

---

## Execution Metadata

**Execution Type:** Canonical  
**Audience:** Builder | Designer | Learner  
**Production Use:** Yes  
**System Dependency:** Required

**Prerequisites:**
- GitHub account and repository access
- AWS account with CodePipeline/CodeCommit access
- Understanding of source control concepts
- Knowledge of webhook and integration patterns
- Basic familiarity with OAuth/authentication
- Understanding of repository structure

**Outputs:**
- GitHub repository connection configuration
- AWS CodePipeline source integration
- Webhook configuration
- Source control validation results
- Integration test evidence

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

This project establishes version control for a Java web app hosted on an AWS EC2 instance by connecting the project directory to a GitHub repository. The objective is to create a clean source-of-truth for code changes, enable repeatable collaboration patterns, and set the foundation for later CI/CD steps that will pull from GitHub.

### Key tools and concepts

Git and GitHub for source control and change history. Amazon EC2 as the development host accessed through VS Code Remote SSH. Core concepts include local repositories, remotes, branches, commits, pushes, and token-based authentication for HTTPS Git operations.

### Project reflection

Took about 1.5 hours. The main friction points were correctly wiring the local repository to the GitHub remote and completing secure authentication after GitHub rejected password-based HTTPS pushes. The key outcome was a working end-to-end workflow where changes made on the EC2-hosted project were committed locally and pushed to GitHub with traceable history.

I completed this project to formalize a standard DevOps workflow: code changes are tracked locally, reviewed via commit history, and synchronized to a remote repository that will later serve as the pipeline source. This is the required prerequisite for downstream build and deployment automation using AWS developer tools.

This work is the second step in a sequential CI/CD buildout. The deliverable for this step is not automated deployment; it is a correctly configured GitHub repository and a repeatable commit and push workflow from the EC2-hosted development environment.

---

## Git and GitHub

Git provides local version control by tracking file changes as commits, enabling rollback, comparison, and auditable history. I installed Git on the EC2 instance using sudo dnf update -y and sudo dnf install git -y to update packages and install the Git client.

GitHub is the remote repository host used to store the project’s code and history off-instance. It enables collaboration, centralized review, and serves as an integration point for CI/CD systems that pull source from the repository.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_efaadbf7)

---

## My local repository

A local Git repository is the .git database that records file states and commit history in the project directory. It enables structured change capture on the EC2 instance before synchronizing those changes to GitHub.

git init initializes the local repository by creating the .git directory. I ran it from the project’s working directory so subsequent edits to project files could be staged, committed, and pushed with version history.

Branches represent independent lines of development by pointing to specific commit snapshots. The terminal message confirming an initialized repository indicates Git is active in the directory and ready to track changes.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

git add . stages changes for the next commit by selecting which file modifications will be included in the snapshot. Staging acts as a controlled gate between editing and committing.

### git commit

git commit -m "..." writes the staged changes into the repository history as an immutable snapshot with a descriptive message. This creates an auditable record of what changed and why.

### git push

git push -u origin master uploads local commits to the remote repository. -u sets upstream tracking so future pushes can use git push without re-specifying the remote and branch.

---

## Authentication

Git requires authentication to prevent unauthorized writes to the remote repository. Over HTTPS, GitHub does not accept account passwords for Git operations; it requires a Personal Access Token (PAT) or another supported auth method. Authentication ensures authorization, attribution, and repository integrity.

### Local Git identity

Git commit metadata includes an author name and email for attribution and auditability. Configuring user.name and user.email ensures commits reflect the correct author rather than instance defaults.

git log displays commit history including commit IDs, author metadata, timestamps, and messages. This provides traceability across changes and supports debugging and review.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub rejected password authentication for HTTPS Git operations, so a Personal Access Token was required to authorize pushes from the EC2-hosted environment.

GitHub tokens are scoped credentials used to authenticate Git operations over HTTPS. In this workflow, the token replaces a password during git push and provides controlled access to the repository based on selected scopes.

Set up a GitHub token by navigating to GitHub Settings, Developer settings, Personal access tokens, then generating a token with the minimum required scope (for this project, repo access). Store the token securely because it cannot be retrieved after leaving the page.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_fa11169d)

---

## Making changes again

Changes made to files were not visible in GitHub until the full version-control sequence was completed: stage the changes (git add), commit them (git commit), and push them to the remote (git push). Saving a file in VS Code only updates the working directory on the EC2 instance, not the GitHub repository.

After staging, committing, and pushing, the updated file appeared in the GitHub repository on refresh, confirming the remote link and authentication flow were correctly configured.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_6becb2bc)

---

## Setting up a READMe file

A README.md file was added to document repository purpose and basic usage. The file was created, committed, and pushed so the repository has an immediate entry point.

Markdown is used for README content because it is a lightweight formatting standard that renders cleanly on GitHub. Common constructs include headings, lists, links, code blocks, and images, which are sufficient for clear project documentation.

README file has 6 sections: project purpose, prerequisites, setup, usage examples, contribution guidelines, and team roles. Each section is direct and structured to reduce ambiguity.

![Image](http://learn.nextwork.org/refreshed_maroon_timid_jujube/uploads/aws-devops-github_c94976902)

---

---

## Navigation

| Previous | Next |
|----------|------|
| [CI/CD Introduction](./01-cicd-introduction.md) | [Environment Bootstrap](./03-environment-bootstrap.md) |