# Proof of Concept (POC) for Unit Testing

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level** | **Reviewer** |
|------------|--------------|-------------|----------------|----------------|-------------|-------------|
| Mohit Kumar | 08-03-2025 | V1 | Mohit Kumar | 08-03-2025 | Internal Reviewer | Komal Jaiswal |

## Table of Contents:
- [Introduction](#introduction)
- [Step-by-Step Setup Guide](#step-by-step-setup-guide)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)

## Introduction

This Proof of Concept (POC) focuses on setting up unit testing in a frontend application using Jest, a widely used JavaScript testing framework. The guide provides a detailed step-by-step process to install and configure Jest, ensuring smooth execution of unit tests.

---

## Step-by-Step Setup Guide

### **Step 1**: Clone the Repository

Clone the frontend repository from GitHub using the following command:

```
git clone https://github.com/OT-MICROSERVICES/frontend.git
```

Move into the project directory:

```
cd frontend/
```
![image](https://github.com/user-attachments/assets/dba41e39-b472-4a53-b47c-59d670b1f6cc)

---

### **Step 2**: Install NPM (if not already installed)

- Install Node Package Manager (NPM):

```
sudo apt install npm
```

- Verify installation:

```
npm -v
```
![image](https://github.com/user-attachments/assets/dc5a0c08-9d23-467d-8c87-ce21f5cbed56)
---

### **Step 3**: Check Jest Version in Your Project

- Open `package.json` inside the `frontend/` directory and check for the Jest version:

```json
"devDependencies": {
  "jest": "23.6.0"
}
```
![image](https://github.com/user-attachments/assets/9cd8f63f-1a0d-45d9-be57-ba97a69f504a)
![image](https://github.com/user-attachments/assets/26164b3f-5adc-478a-bf4b-a5a6ed26ed22)

- If Jest is already listed, install the specified version:

```
npm install --save-dev jest@23.6.0 babel-jest@23.6.0
```

- If Jest is missing, add it manually:

```
npm install --save-dev jest@23.6.0 babel-jest@23.6.0
```
![image](https://github.com/user-attachments/assets/25936dcf-55b4-476f-83c0-d1734f9ff47a)

- Verify the installation:

```
npx jest --version
```
![image](https://github.com/user-attachments/assets/9aac2452-3aa4-4051-bd86-247b014268f4)


📌 **Why use `npx` instead of `npm`?**
- `npx` runs commands directly from `node_modules` without requiring a global installation.
- `npm` installs packages, whereas `npx` executes commands.

---

### **Step 4**: Update `package.json`

Ensure the `package.json` file has the following test script:

```json
"scripts": {
  "test": "jest"
}
```

![image](https://github.com/user-attachments/assets/b3bfb260-06f0-4f80-82ea-62c56dce95f0)


📌 **Why is this step important?**
- This allows you to run tests using `npm test` instead of `npx jest`.
- If missing, Jest won't execute via `npm test`.
- Add the above snippet inside the `scripts` section if it’s not present.

---

### **Step 5**: Run Jest Tests

Run the following command to execute Jest tests:

```
npm test
```
![image](https://github.com/user-attachments/assets/b7460c5b-1cee-4ee3-a6d6-e424656da9c6)

If Jest does not detect test files, ensure they follow the proper naming conventions:
- `*.test.js` (e.g., `Component.test.js`)
- `*.spec.js` (e.g., `Utility.spec.js`)
- Tests placed inside a `__tests__` directory

---

### **Step 6**: Clear Jest Cache (if tests do not execute)

If Jest fails to detect tests, clear the cache and retry:

```
npx jest --clearCache
npm test
```

---

## Conclusion

Unit testing plays a crucial role in maintaining the stability of a frontend application. By integrating Jest, we ensure efficient testing of components and functions, reducing the chances of bugs. Follow the steps outlined above to set up Jest seamlessly and run tests effectively, making the frontend codebase robust and maintainable.

---

## Contact Information

| Name | Email Address |
|------|--------------|
| Mohit Kumar | Mohit.kumar@mygurukulam.co |

---

## References

| Link | Description |
|------|------------|
| [**Jest Official Documentation**](https://jestjs.io/docs/getting-started) | Comprehensive Jest documentation for installation, setup, and advanced usage. |
| [**Jest Testing Guide**](https://jestjs.io/docs/tutorials) | Beginner-friendly guide to writing unit tests using Jest. |

