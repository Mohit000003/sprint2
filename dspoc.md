# Proof of Concept (PoC)
![image](https://github.com/user-attachments/assets/3f35a99f-097e-41af-8226-ba77fb80fbc3)



## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Step 1: Download OWASP Dependency Check (Version 8.4.0)](#step-1-download-owasp-dependency-check-version-840)
  - [Step 2: Extract the Downloaded File](#step-2-extract-the-downloaded-file)
  - [Step 3: Navigate to the Extracted Directory](#step-3-navigate-to-the-extracted-directory)
  - [Step 4: Verify Installation](#step-4-verify-installation)
- [Clone the Repository](#clone-the-repository)
- [Run OWASP Dependency Check](#run-owasp-dependency-check)
- [View the Report](#view-the-report)
    - [Step 1: Download the Google Chrome .deb Package](#step-1-download-the-google-chrome-deb-package)
    - [Step 2: Install Google Chrome](#step-2-install-google-chrome)
    - [Step 3: Open the Report in Google Chrome](#step-3-open-the-report-in-google-chrome)
- [Contact Information](#contact-information)
- [References](#references)

___

## Introduction
[OWASP Dependency Check](https://owasp.org/www-project-dependency-check/) is a security tool that analyzes project dependencies to identify publicly known vulnerabilities. It helps detect dependencies with security issues by referencing the National Vulnerability Database (NVD).

This **Proof of Concept (PoC)** demonstrates how to set up and run **OWASP Dependency Check** on the `employee-api` repository, generating a security report for further analysis.

---

## Prerequisites

Ensure the following dependencies are installed before proceeding:

| Requirement | Description |
|------------|-------------|
| **Git** | Required to clone the repository. |
| **Java** | Needed to run OWASP Dependency Check. Ensure Java 8 or later is installed. |
| **Unzip** | Required to extract the OWASP Dependency Check package. |


---

## Installation

### **Step 1: Download OWASP Dependency Check (Version 8.4.0)**
```bash
curl -sLO https://github.com/jeremylong/DependencyCheck/releases/download/v8.4.0/dependency-check-8.4.0-release.zip
```
### **Step 2: Extract the downloaded file**
```bash
unzip dependency-check-8.4.0-release.zip
```

![image](https://github.com/user-attachments/assets/b562e7d9-43bf-40ff-ada8-dbf4138b7cfb)

### **Step 3: Navigate to the extracted directory**
```
cd dependency-check
or
cd dependency-check-8.4.0
```
- (depending on the extracted folder name)

### **Step 4 :Verify installation**
```
./bin/dependency-check.sh --version
```
![image](https://github.com/user-attachments/assets/b65f52c9-45ab-4b83-8851-23e004cd0260)


___

 ## Clone the Repository
Clone the `employee-api` repository where the dependency check will be performed.
```bash
git clone https://github.com/OT-MICROSERVICES/employee-api.git
cd employee-api
```
![image](https://github.com/user-attachments/assets/d3c487a2-4bbd-42dc-9b84-ef859b685387)

---

## Run OWASP Dependency Check

Run the security scan inside the **employee-api** directory:
```bash
../dependency-check/bin/dependency-check.sh \
  --project "employee-api" \
  --scan . \
  --format HTML \
  --out security-reports
```

### **Explanation of Flags:**
- `--project "employee-api"` → Sets the project name for the report.
- `--scan .` → Scans all dependencies in the current directory.
- `--format HTML` → Generates the report in an **HTML** format for easy viewing.
- `--out security-reports` → Saves the report inside the `security-reports/` directory.

---

![image](https://github.com/user-attachments/assets/4ff88692-f855-4527-9c11-442d087e0cef)
![image](https://github.com/user-attachments/assets/2f27719f-99bb-48a6-8cb1-64e4611bfa43)


## View the Report

### Step 1: Download the Google Chrome .deb Package
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```
### Step 2: Install Google Chrome
  
```
sudo apt install ./google-chrome-stable_current_amd64.deb
```
### Open the Report in Google Chrome
```
google-chrome security-reports/dependency-check-report.html &
```

![image](https://github.com/user-attachments/assets/5d9191cf-fec4-4998-905f-374722bc1552)

___

## **Contact Information**

| **Name** | **Email address**            |
|----------|-------------------------------|
| Mohit kumar   |  mohit.kumar@mygurukulam.co          |
___

## References

| Reference | Description |
|-----------|-------------|
| [OWASP Dependency Check Documentation](https://jeremylong.github.io/DependencyCheck/) | Official documentation for OWASP Dependency Check. |
| [National Vulnerability Database (NVD)](https://nvd.nist.gov/) | The vulnerability database referenced by Dependency Check. |
| [GitHub - OWASP Dependency Check](https://github.com/jeremylong/DependencyCheck) | Official GitHub repository for the project. |

___
