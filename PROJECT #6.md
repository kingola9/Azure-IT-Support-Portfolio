# 🔐 PROJECT 6: Set Up New Employee Access with Microsoft Entra ID & Azure RBAC

## 📌 Project Overview

This guided project demonstrates hands-on identity and access management skills in Microsoft Azure by onboarding a new employee using **Microsoft Entra ID** and implementing **Role-Based Access Control (RBAC)** using the principle of **least privilege**.

The project involved creating a new user account, organizing permissions through a security group, assigning access at the correct Azure scope, validating access boundaries, and removing resources after testing.

This simulates a real-world IT Support / Cloud Administrator task where new employees require secure and controlled access to company resources.

---

## 🌍 Real-World Scenario

A growing company hires a new **IT Support Engineer** who needs access to manage virtual machines and monitor resources for the Support Team.

Instead of giving direct subscription-wide admin rights, the company creates:

- A company user account in Microsoft Entra ID  
- A Support Team security group  
- RBAC access only to the **IT-Support Resource Group**

This ensures the employee can perform assigned duties without accessing finance systems, production databases, or unrelated departments.

This is how professional organizations reduce security risks while improving onboarding speed.

---

## 🎯 Objectives Achieved

✔ Created a new user account in Microsoft Entra ID  
✔ Created a security group for permission management  
✔ Added the user to the group  
✔ Assigned RBAC permissions at **Resource Group scope**  
✔ Verified access rights were limited correctly  
✔ Practiced least-privilege access design  
✔ Removed users, roles, and test resources after completion  

---

## 🛠 Technologies & Services Used

- Microsoft Azure Portal  
- Microsoft Entra ID (Azure AD)  
- Azure Role-Based Access Control (RBAC)  
- Azure Resource Groups  
- Identity & Access Management (IAM)  
- Security Groups  

---

## 🔍 Implementation Process

### 1️⃣ Created New Employee User in Microsoft Entra ID

A new user account was created to simulate onboarding a staff member.

**Technical Reason:**  
Entra ID provides centralized identity management for sign-in, MFA, password policies, and audit tracking.

---

### 2️⃣ Created Security Group for Access Management

A security group was created and the user was added.

**Technical Reason:**  
Groups simplify administration by allowing multiple users to inherit the same permissions without assigning access individually.

---

### 3️⃣ Assigned Azure RBAC Role at Resource Group Scope

The security group was assigned a built-in RBAC role at the **Resource Group** level.

Example roles:

- Reader  
- Contributor  
- Virtual Machine Contributor  

**Technical Reason:**  
Scoping access to a resource group prevents unnecessary subscription-wide privileges and limits operational impact.

---

### 4️⃣ Verified Least-Privilege Access Model

Access was tested to ensure the user could perform required tasks only.

**Technical Reason:**  
Validation confirms correct permissions while blocking unauthorized actions.

---

### 5️⃣ Cleaned Up Users, Roles & Resources

Temporary accounts, groups, and permissions were removed.

**Technical Reason:**  
Unused accounts and stale permissions create security exposure and governance issues.

---

## 🧠 Key Skills Demonstrated

- User onboarding & offboarding  
- Microsoft Entra ID administration  
- Azure RBAC management  
- Least privilege security implementation  
- Group-based access control  
- Scope-based permission design  
- Security validation  
- Identity governance  

---

## 💼 Business Value

This project demonstrates the ability to help organizations:

- Onboard employees faster  
- Reduce over-permissioned accounts  
- Standardize access control  
- Improve compliance readiness  
- Protect sensitive cloud resources  
- Reduce admin overhead through group-based management  

---

## 📷 Suggested Screenshots for Portfolio

- Entra ID Users page  
- Security Group creation  
- Group membership page  
- IAM Role Assignment page  
- Resource Group access control  
- Permission verification  
- Cleanup confirmation  

---

## 🚀 Why This Project Matters

This project proves practical knowledge of how companies securely grant employee access in Azure environments.

It demonstrates readiness for roles such as:

- IT Support Specialist  
- Azure Administrator  
- Help Desk Analyst  
- Cloud Support Engineer  
- IAM Analyst  

---

## 📚 Key Takeaway

I learned how to securely onboard users in Azure using **Microsoft Entra ID** and **RBAC**, ensuring each employee receives only the access required to do their job while protecting company resources.

---

## 📚 Author

**Abeeb Olabode**

IT Support / Cloud Support Professional
