# Proof of Concept | Commit Sign-off


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   25-02-2025        | V1   | Mohit Kumar |25-02-2025    |  Internal Reviewer | Komal Jaiswal |

## Table of Contents

- [Prerequisites](#prerequisites)
- [Step-by-Step Installation Guide](#step-by-step-installation-guide)
- [Contact Information](#contact-information)
- [References](#references)
***
## Prerequisites


Before using commit sign-off, ensure you have the following:

| Requirement            | Description |
|------------------------|-------------|
| **Git Installed**      | Ensure you have Git installed on your system. Check with:  ```  git --version ``` |
| **Configured Git User** | Set up your name and email in Git:  ```  git config --global user.name "Your Name"  git config --global user.email "your.email@example.com" ``` |
| **Access to a Repository** | Ensure you have access to a Git repository where you can commit changes. |
| **CI/CD Pipeline Setup (Optional)** | If using automated validation, ensure your CI/CD pipeline supports commit sign-off verification. |

## Step-by-Step Installation Guide

### 1. **Configure Git (One-Time Setup)**
Before you start using commit sign-off, configure your Git   username and email:
 ``` bash
 git config --global user.name "Your Name"
 git config --global user.email "your.email@example.com"
 ```
![image](https://github.com/user-attachments/assets/b18c1390-9aa6-4411-9498-02d2c2d089d5)


This setup ensures that every commit you make includes your name and email.

### 2. **Verify the configuration:-**
  
``` bash
    git config --list
```
![image](https://github.com/user-attachments/assets/470ee93f-d59b-4b9b-8336-bd8dc46273f3)


   This command will show you the settings to confirm that your username and email have been configured correctly.

### 3. **Clone the Repository and Navigate to It**
```bash
git clone <repository-url>
cd <repository-name>
```
Replace `<repository-url>` with the actual URL of your repository and `<repository-name>` with the name of the cloned directory.
![image](https://github.com/user-attachments/assets/e17ddf14-8ea0-4846-a3b5-5f76e86f793e)
![image](https://github.com/user-attachments/assets/83952183-45c8-48fe-8611-081733c96d5b)






### 4. **Stage Your Changes**
```bash
git add .
```
![image](https://github.com/user-attachments/assets/1026a75b-ddd2-45db-b16a-d2f0de54d15d)

This adds all modified and new files to the staging area before committing.


### 5. **Commit with Sign-Off:-**
Use the -s flag while committing to automatically append the sign-off line:
```
git commit --signoff -m "Your commit message"
```
![image](https://github.com/user-attachments/assets/35ec24c4-ee9c-495e-864d-4d8a8cb20b98)



The -s flag adds a Signed-off-by line at the end of the commit message, indicating that you acknowledge the contribution under the Developer Certificate of Origin (DCO).


### 4. **Verify the Sign-Off:-**
 
To check whether the commit is signed off, use the following command:
```
git log -1
```

This will display the latest commit details, including the sign-off message:
![image](https://github.com/user-attachments/assets/fb0a95a6-3b9e-4460-ba3c-a225dcd55fa9)


If the Signed-off-by line appears in the commit message, your commit is properly signed off.

### 5. **Push Your Commit:-**
After verifying, push the commit to the remote repository:
```
git push origin main  # Replace 'main' with your branch name if different
```
![image](https://github.com/user-attachments/assets/026269c7-7d57-4d42-8e3e-643181a25562)

This will upload your signed-off commit to the repository.

![image](https://github.com/user-attachments/assets/0c3d4d47-ecac-404d-adde-c5a60b09e3ed)



## Contact Information


| **Name** | **Email address**            |
|----------|-------------------------------|
| Mohit kumar   |  mohit.kumar@mygurukulam.co          |


## References

| Resource                                  | Link                                                       |
|-------------------------------------------|------------------------------------------------------------|
| |
| GitHub's Commit Signing Guide             | [https://docs.github.com/en/authentication/managing-commit-signature-verification](https://docs.github.com/en/authentication/managing-commit-signature-verification) |



***

