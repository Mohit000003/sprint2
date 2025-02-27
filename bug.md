# Commit Sign-Off - Detailed Documentation


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   25-02-2025        | V1   | Mohit Kumar |25-02-2025    |  Internal Reviewer | Komal Jaiswal |

## Table of Contents

- [Introduction](#introduction)
- [What is Commit Sign-Off?](#what-is-commit-sign-off)
- [Why We Use It](#why-we-use-it)
- [Tools for Commit Sign-Off](#tools-for-commit-sign-off)
- [Advantages](#advantages)
- [Proof of Concept (POC)](#proof-of-concept-poc)
- [Best Practices](#best-practices)
- [Recommendation/Conclusion](#recommendationconclusion)
- [Contact Information](#contact-information)
- [References](#references)

---

## Introduction


This document explains **commit sign-offs**, why they're important for accountability and compliance, and how to use them in your workflow to follow project rules and legal guidelines.



---

## What is Commit Sign-Off?

Commit sign-off is a process where a developer includes a "Signed-off-by" line in their commit message. This line typically includes the developer's name and email, acknowledging that they have read and agree to the project's contribution policies. This is especially important in open-source projects to ensure that all contributions meet legal and compliance standards.

---

## Why We Use It

- **Confirms Authorship** – Identifies who wrote the code.
- **Ensures Compliance** – Helps enforce project guidelines and legal policies (e.g., Developer Certificate of Origin - DCO).
- **Improves Traceability** – Maintains a transparent development history.
- **Supports CI/CD** – Enables automated checks for compliance before merging.

---

## Tools for Commit Sign-Off


| Tool             | What It Does                                                                                                   |
|------------------|----------------------------------------------------------------------------------------------------------------|
| **Git**          | Git itself allows you to sign off your commits using the -s flag. When you run `git commit -s -m "Your message"`, it automatically adds a "Signed-off-by" line with your name and email. This shows that you agree to the commit and take responsibility for it. |
| **Git Hooks**    | These are small scripts that run automatically before or after certain Git actions. You can set up a **pre-commit hook** to block commits that don't have a sign-off, ensuring that every commit follows the required policy. |
| **DCO Bot**      | This is a bot used in GitHub repositories to check if all commits in a pull request (PR) are properly signed off. If a commit is missing a sign-off, the bot will leave a comment asking the author to fix it before merging the PR. |
| **CI/CD Pipelines** | Continuous Integration/Continuous Deployment (CI/CD) tools like Jenkins, GitHub Actions, and GitLab CI/CD can be set up to **automatically verify** commit sign-offs. If a commit does not have a sign-off, the pipeline can **fail the build** or reject the changes. |

---



## Advantages

- **Increased Accountability** – Developers are directly accountable for their contributions.
- **Legal Compliance** – Ensures that commits comply with the Developer Certificate of Origin (DCO) and any legal policies.
- **Better Collaboration** – Helps maintain a clean and clear history of who contributed what and when.
- **Prevents Unauthorized Changes** – By ensuring compliance, it prevents unauthorized or accidental changes to the project.
- **Easier Audits** – Simplifies the process of auditing commit history for compliance or code review.

---

## Proof of Concept (POC)

For Detailed Documentation Follow this link: [Commit Sign-Off Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Mohit-SCRUM-64/Application%20CI%20Design/Generic%20CI%20operation/Commit%20Sign%20off/POC/README.md)

---

## Best Practices

| ✅ **Best Practice** | **Description**                                                                                       |
|----------------------|------------------------------------------------------------------------------------------------------|
| **Always sign off commits using -s** | Ensures every commit includes a valid Signed-off-by line. |
| **Use Git hooks to enforce sign-offs locally** | Automate sign-off checks before committing code. |
| **Automate checks in CI/CD pipelines** | Use tools like **DCO Bot** to prevent unsigned commits from merging. |
| **Keep your name & email correctly configured in Git** | Run the following to ensure accurate commit attribution:<br> ```sh<br>git config --global user.name "Your Name"<br>git config --global user.email "your.email@example.com"<br>``` |
| **Follow the project’s contribution guidelines** | Different repositories may have specific requirements. |
| **Educate contributors on sign-offs** | Ensure all team members understand its importance. |
| **Regularly audit commit history** | Periodically review past commits for compliance. |
| **Use pre-commit hooks for validation** | Prevent unsigned commits before they are made. |

---

## Recommendation/Conclusion

Commit sign-off helps keep track of who contributed to a project and ensures that everyone follows the rules. It improves security, makes the development process more transparent, and prevents unauthorized changes.  

By using **Git** with the `-s` flag for commit sign-offs, along with tools like **Git hooks** and **CI/CD pipelines**, teams can **automate checks, enforce compliance, and maintain a smooth and secure workflow**. A simple `-s` flag while committing can make a big difference in keeping projects organized, secure, and trustworthy.


---

## Contact Information

| **Name**        | **Email address**            |
|-----------------|------------------------------|
| Mohit Kumar     | mohit.kumar@mygurukulam.co    |

---

## References

| Resource                                  | Link                                                       |
|-------------------------------------------|------------------------------------------------------------|
| Developer Certificate of Origin (DCO)     | [Developer Certificate](https://developercertificate.org/) |
| Git Commit Documentation                  | [Git Commit Docs](https://git-scm.com/docs/git-commit) |
| Why Signed Commits Matter                 | [Contributor Covenant](https://www.contributor-covenant.org/) |
