# Proof of Concept | Bug Analysis
![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTCUw8YTFHb305eWBPpibrvVTOSijntvbRZQA&s)

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   26-02-2025        | Version 1   | Mohit Kumar |26-02-2025    |  Internal Reviewer | Komal Jaiswal |

## Table of Contents

- [Prerequisites](#prerequisites)
- [Step-by-Step Installation Guide](#step-by-step-installation-guide)
- [Contact Information](#contact-information)
- [References](#refrences)
***
## Prerequisites

| Component                | Requirement Description                                      |
|--------------------------|--------------------------------------------------------------|
| **Go Environment**       | Ensure Go is installed. Download it from the [official site](https://go.dev/dl/). |
| **Go Project**           | Set up a Go project with the necessary structure and modules. |
| **Sufficient Resources** | Ensure your system has at least **2GB of RAM**.             |
___

## Step-by-Step Installation Guide

Follow these steps to perform bug analysis using `golangci-lint`:

### 1.Update and Install Go
``` bash
sudo apt update
sudo apt install golang -y
```
 ### 2. Check for the version
``` bash
  go version
```
### 3. Clone the Repository

```sh
# Clone the repository to analyze

git clone git@github.com:OT-MICROSERVICES/employee-api.git
cd employee-api
```
![image](https://github.com/user-attachments/assets/61a99696-f359-4d0f-960d-6c7752143ea6)

### 4. Install golangci-lint
```sh
# Install golangci-lint

curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s latest
```


### 5. Run Bug Analysis
```sh
# Run golangci-lint to check for bugs and issues

golangci-lint run ./...
```
![image](https://github.com/user-attachments/assets/13b5e8e2-cec0-4402-b0dc-fac3e54e450a)


___

## **Contact Information**

| **Name** | **Email address**            |
|----------|-------------------------------|
| Mohit kumar   |  mohit.kumar@mygurukulam.co          |

## References 

| Resource                | Link |
|-------------------------|------|
| **GoLang Official Documentation** | [Visit](https://golang.org/doc/) |


***
