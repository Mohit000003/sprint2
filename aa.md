# SonarQube Authentication and Authorization

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   25-02-2025        | V1   | Mohit Kumar |25-02-2025    |  Internal Reviewer | Komal Jaiswal |


## Table of Contents
- [Introduction](#introduction)
- [What is Authentication and Authorization?](#what-is-authentication-and-authorization)
- [Why Do We Use Authentication and Authorization?](#why-do-we-use-authentication-and-authorization)
- [Authentication Methods](#authentication-methods)
- [Authorization Methods](#authorization-methods)
- [Best Practices](#best-practices)
- [FAQ](#faq)
- [Conclusion](#conclusion)
- [References](#references)
___
## Introduction
SonarQube provides robust authentication and authorization mechanisms to secure access to its projects and features. It supports multiple authentication methods and fine-grained permission control.

## What is Authentication and Authorization?
- **Authentication** verifies who you are (identity validation).
- **Authorization** defines what you can do (permission assignment).

**Example:** When logging into SonarQube:
- Authentication ensures you are a valid user.
- Authorization determines whether you can modify settings or only view reports.
___
## Why Do We Use Authentication and Authorization?
- **Security:** Prevents unauthorized access to code analysis and reports.
- **Access Control:** Ensures users only access relevant projects and features.
- **Compliance:** Helps meet industry security and compliance standards.
___
## Authentication Methods
SonarQube supports various authentication methods for flexibility in integration.

| Authentication Method | Description | UI Configuration | Server Configuration |
|----------------------|-------------|-----------------|----------------------|
| **Built-in Users/Groups Database** | SonarQube's internal authentication system, storing user credentials securely. The default username and password are `admin/admin`, set by the database. | Managed via `Administration > Security > Users` | Users are stored in SonarQube’s internal database, no additional setup required. |
| **LDAP (Lightweight Directory Access Protocol)** | Allows integration with enterprise directory services for centralized authentication. | Enable LDAP authentication in `Administration > Security > LDAP` | Modify `sonar.properties` to include LDAP connection details and restart SonarQube. |
| **SAML (Security Assertion Markup Language)** | Enables Single Sign-On (SSO) using identity providers like Okta or Azure AD. | Configured in `Administration > Security > SAML` | Requires setting `sonar.auth.saml.*` properties in `sonar.properties`. |
| **HTTP Headers** | Authenticates users via a reverse proxy that passes user credentials. | Managed via reverse proxy settings | Configure the reverse proxy to pass authentication details. |
| **GitHub, GitLab, Bitbucket Cloud** | Uses OAuth authentication via third-party developer platforms. | Set up OAuth in `Administration > Security > OAuth` | Requires registering the application with the respective provider. |
___
## Authorization Methods
SonarQube assigns permissions based on users and groups.

| Authorization Method | Description | UI Configuration | Server Configuration |
|---------------------|-------------|-----------------|----------------------|
| **User and Group Management** | Users and groups are created and managed within SonarQube. | Managed in `Administration > Security > Users and Groups` | Users can be assigned to groups, and permissions can be set per group. |
| **Permission Assignment** | Granular permissions can be assigned to users and groups for different actions. | Permissions are set in `Administration > Security > Permissions` | Controls project and feature access based on roles and permissions. |
| **Default Groups** | SonarQube has predefined groups like `sonar-users` for new users. | Managed in `Administration > Security > Groups` | `Anyone` includes all users, and `sonar-users` is the default group for new users. |
| **Tokens** | Used for secure API authentication and authorization instead of passwords. | Managed via `Administration > Security > Users > Tokens` | Tokens are securely stored in SonarQube’s database and must be regenerated when expired. |
___
## Best Practices
- Use **LDAP or SAML** for centralized authentication.
- Apply **principle of least privilege** to permissions.
- Enable **two-factor authentication (2FA)** where possible.
- Regularly audit **user access logs**.
- Use **tokens** for API access instead of password-based authentication.
___
## FAQ
### Q1: What is the default authentication and authorization behavior in SonarQube?
- **Authentication:** SonarQube uses a built-in user database by default, where the default username and password are `admin/admin`, set by the database.
- **Authorization:** New users are added to the `sonar-users` group, which has limited permissions.
- **Forced Authentication:** By default, users must log in to access any part of SonarQube. If anonymous access is disabled, all users must authenticate before viewing any content. Forced authentication means that every user must go through the authentication process before gaining access to SonarQube's features, preventing unauthorized users from viewing or modifying data.
- **Full Permissions:** To grant full permissions, users must be added to `sonar-administrators`.

### Q2: Can I use multiple authentication providers at the same time?
- Yes, SonarQube allows multiple authentication integrations simultaneously, such as LDAP and GitHub OAuth.

### Q3: How does SonarQube handle expired authentication tokens?
- Expired tokens are automatically revoked, and users must generate a new one.

### Q4: Does SonarQube support Single Sign-On (SSO)?
- Yes, via SAML, LDAP, or OAuth integrations.
___
## Conclusion
SonarQube provides a flexible authentication and authorization system, integrating with multiple identity providers. It allows organizations to manage access control securely and efficiently.
___
## References


| **Link** | **Description** |
|------------------------------------------------------|------------------|
| [SonarQube Documentation](https://docs.sonarqube.org/) |Sonar Official Documentation
| [Authentication](https://www.sonarsource.com/blog/sonarqube-ldap-sso/)| Sonar authentication and authorization |
| [Authentication and Authorization](https://docs.sonarsource.com/sonarqube-server/9.9/instance-administration/authentication/overview/#:~:text=SonarQube%20comes%20with%20an%20onboard,for%20Bitbucket%2C%20and%20authentication.)| Sonar authentication and authorization|

___
