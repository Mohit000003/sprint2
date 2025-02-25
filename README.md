
# **Commit Sign-Off Documentation**



| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   25-02-2025        | Version 1   | Mohit Kumar |25-02-2025    |  Internal Reviewer | Komal Jaiswal |

# Table of Contents
- [Introdcution](#introduction)
- [Pre-Requisites](#pre-requisites)
- [What is Commit Sign-Off ?](#what-is-commit-sign-off)
- [Why We Use It](#why-we-use-it)
- [Tools to Use](#tools-to-use)
- [Proof of Concept (POC)](#proof-of-concept-poc)
- [Best Practices](#best-practices)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)  
- [References](#references)  


# Introduction
This document provides a comprehensive guide on commit sign-off, explaining its importance, usage, and integration into CI/CD pipelines. It covers the tools available for commit sign-off, best practices, and how to ensure compliance with project guidelines.



# Pre-Requisites
Before using commit sign-off, ensure you have the following:

- **Git Installed** – Ensure you have Git installed on your system. You can check by running:
``` bash
git --version
```

- **Configured Git User** – Set up your name and email in Git:
``` bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

- **Access to a Repository** – You should have access to a Git repository where you can commit changes.

- **CI/CD Pipeline Setup (Optional)** – If using automated validation, ensure your CI/CD pipeline supports commit sign-off verification.

# What is Commit Sign-Off?
Commit sign-off is a way for developers to certify that they are the author of a commit and agree to the project’s contribution guidelines. It is done by adding a Signed-off-by line in the commit message.

``` bash
Signed-off-by: Your Name <your.email@example.com>
```

This acts as a **digital signature**, ensuring accountability and compliance with the project’s contribution policies.

# Why We Use It

- **Confirms Authorship** – Identifies who wrote the code.

- **Ensures Compliance** – Helps enforce project guidelines and legal policies (e.g., Developer Certificate of Origin - DCO).

- **Improves Traceability** – Maintains a transparent development history.

- **Supports CI/CD** – Enables automated checks for compliance before merging.

# Tools to Use 

| Tool | What It Does |  
|------|-------------|  
| **Git** | Git itself allows you to sign off your commits using the `-s` flag. When you run `git commit -s -m "Your message"`, it automatically adds a "Signed-off-by" line with your name and email. This shows that you agree to the commit and take responsibility for it. |  
| **Git Hooks** | These are small scripts that run automatically before or after certain Git actions. You can set up a **pre-commit hook** to block commits that don't have a sign-off, ensuring that every commit follows the required policy. |  
| **DCO Bot** | This is a bot used in GitHub repositories to check if all commits in a pull request (PR) are properly signed off. If a commit is missing a sign-off, the bot will leave a comment asking the author to fix it before merging the PR. |  
| **CI/CD Pipelines** | Continuous Integration/Continuous Deployment (CI/CD) tools like Jenkins, GitHub Actions, and GitLab CI/CD can be set up to **automatically verify** commit sign-offs. If a commit does not have a sign-off, the pipeline can **fail the build** or reject the changes. |


# Proof of Concept (POC)

### 1. **Configure Git (One-Time Setup)**
Before you start using commit sign-off, configure your Git   username and email:
 ``` bash
 git config --global user.name "Your Name"
 git config --global user.email "your.email@example.com"
 ```
This setup ensures that every commit you make includes your name and email.

### 2. **Verify the configuration:-**
  
``` bash
    git config --list
```
   This command will show you the settings to confirm that your username and email have been configured correctly.

### 3. **Commit with Sign-Off:-**
Use the -s flag while committing to automatically append the sign-off line:
```
git commit --signoff -m "Your commit message"
```
The -s flag adds a Signed-off-by line at the end of the commit message, indicating that you acknowledge the contribution under the Developer Certificate of Origin (DCO).

### 4. **Verify the Sign-Off:-**
 
To check whether the commit is signed off, use the following command:
```
git log -1
```
This will display the latest commit details, including the sign-off message:



If the Signed-off-by line appears in the commit message, your commit is properly signed off.

### 5. **Push Your Commit:-**
After verifying, push the commit to the remote repository:
```
git push origin main  # Replace 'main' with your branch name if different
```
This will upload your signed-off commit to the repository.

#  Best Practices

| ✅ **Best Practice** | **Description** |
|----------------------|---------------|
| **Always sign off commits using `-s`** | Ensures every commit includes a valid `Signed-off-by` line. |
| **Use Git hooks to enforce sign-offs locally** | Automate sign-off checks before committing code. |
| **Automate checks in CI/CD pipelines** | Use tools like **DCO Bot** to prevent unsigned commits from merging. |
| **Keep your name & email correctly configured in Git** | Run the following to ensure accurate commit attribution:<br>```sh<br>git config --global user.name "Your Name"<br>git config --global user.email "your.email@example.com"<br>``` |
| **Follow the project’s contribution guidelines** | Different repositories may have specific requirements. |
| **Educate contributors on sign-offs** | Ensure all team members understand its importance. |
| **Regularly audit commit history** | Periodically review past commits for compliance. |
| **Use pre-commit hooks for validation** | Prevent unsigned commits before they are made. |


# Contact Information

| **Name** | **Email address**            |
|----------|-------------------------------|
| Mohit kumar   |  mohit.kumar@mygurukulam.co          |


# References

| Resource                                  | Link                                                       |
|-------------------------------------------|------------------------------------------------------------|
| |
| Git Commit Documentation                  | [https://git-scm.com/docs/git-commit](https://git-scm.com/docs/git-commit) |
| Why Signed Commits Matter                 | [https://www.contributor-covenant.org/](https://www.contributor-covenant.org/) |
| GitHub's Commit Signing Guide             | [https://docs.github.com/en/authentication/managing-commit-signature-verification](https://docs.github.com/en/authentication/managing-commit-signature-verification) |
