# PROJECT 4: 🔐 Azure Resource Organization & Protection with Tags and Locks

## 📌 Project Overview
This project demonstrates how to organize and secure cloud resources in Microsoft Azure using resource tags and resource locks.

It simulates a production-like environment where resources must be:
- Properly labeled for cost tracking and ownership  
- Protected against accidental deletion or modification  

Focus: Azure governance, control, and operational safety.

---

## 🚀 Scenario (Real-World Context)
In enterprise environments, multiple teams share cloud infrastructure.  
Without governance controls:
- Resources may be deleted accidentally  
- Costs become difficult to track  
- Ownership is unclear  

This project implements governance best practices to prevent these risks.

---

## 🎯 Key Objectives
- Apply structured resource tagging strategy  
- Enforce resource protection using locks  
- Validate lock enforcement behavior  
- Demonstrate safe resource lifecycle management  

---

## 🧰 Tools & Technologies
- Microsoft Azure  
- Azure Resource Manager (ARM)  
- Azure Tags  
- Azure Resource Locks  
- Azure Portal  
- Azure CLI  

---

## 🏗️ Architecture & Technical Insight

### Azure Tags
Tags are key-value pairs attached to resources and managed via Azure Resource Manager (ARM).

**Use Cases:**
- Cost allocation  
- Resource organization  
- Automation triggers  

---

### Azure Resource Locks
Locks are enforced at the Azure control plane level, meaning:
- They prevent actions before they reach the resource  
- Even users with high permissions are restricted  

**Types of Locks:**
- CanNotDelete → Blocks deletion  
- ReadOnly → Blocks both deletion and modification  

---

### Lock Inheritance
- Locks applied at the resource group level are inherited by all resources inside it  
- Ensures consistent protection across environments  

---

## ⚙️ Implementation Steps (With Technical Reasoning)

### 1. Create Resources & Apply Tags
- Created resources within a resource group  
- Applied structured tags:

```
Department: Development
Environment: Test

```

**Why this matters:**
- Enables filtering, automation, and cost tracking  
- Improves operational visibility in large environments


<img width="auto" height="auto" alt="Screenshot (260)" src="https://github.com/user-attachments/assets/71a592ea-25c6-4dc5-b0ec-6866e3462f72" />

_**Created a resource group and a storage account inside it**_

---

<img width="auto" height="auto" alt="Screenshot (267)" src="https://github.com/user-attachments/assets/d8788b08-5d72-4783-a072-e3a08c49335d" />

 _**Applied tags to the storage account**_

 ---

<img width="auto" height="auto" alt="Screenshot (265)" src="https://github.com/user-attachments/assets/ebc532dc-674b-48a1-944f-7cce6a9fec66" />

 _**Applied tags to the resource group**_

---

### 2. Apply Resource Locks
- **Applied:**
  - CanNotDelete lock  
  - ReadOnly lock  

**Technical Insight:**
- Locks override RBAC permissions at the control plane level  
- Prevent accidental or unauthorized changes


<img width="auto" height="auto" alt="Screenshot (345)" src="https://github.com/user-attachments/assets/af7874d2-84e8-42ab-b3cc-49fa86d97ff2" />

_**Applied `Delete lock` to the storage acccount to prevent accidental deletion**_

---

<img width="auto" height="auto" alt="Screenshot (348)" src="https://github.com/user-attachments/assets/26758be7-7f0b-40e8-8e7f-6b880e88f7f7" />

_**Applied `Read-Only Lock` to the resource group to prevent modifications.**_

---

### 3. Test Lock Enforcement
**Attempted:**
- Resource deletion  
- Resource modification  

Operations failed due to active locks.

**What this proves:**
- Azure enforces governance policies strictly  
- Protection works even under admin-level access

<img width="auto" height="auto" alt="Screenshot (284)" src="https://github.com/user-attachments/assets/b68b32b2-f203-4d90-96c7-41b1cc772040" />

_**Attempted to modify the resource group by adding another tag but couldn't due to the `Read-Only lock` enforcement**_

---

<img width="auto" height="auto" alt="Screenshot (350)" src="https://github.com/user-attachments/assets/7c0a7d33-c95c-4aa8-8b9c-e1558c9dbe0d" />

_**Attempted to delete the storage account but couldn't due to the `Delete lock` enforcement.**_

---

### 4. Validate Configuration
- **Verified:**
  - Tags are correctly applied  
  - Locks are active  
- Confirmed expected system behavior

<img width="auto" height="auto" alt="Screenshot (265)" src="https://github.com/user-attachments/assets/8103c571-8fd2-416d-b8e4-17a141ee911c" />

_**Tags are correctly applied**_

---

<img width="auto" height="auto" alt="Screenshot (349)" src="https://github.com/user-attachments/assets/25c2630d-a7ce-49b2-841a-f4759bb173b7" />

_**Locks are active in the storage account & resource group**_

---

### 5. Clean Up Resources
- Removed locks before deletion  
- Deleted resources  

**Why this matters:**
- Locks must be removed before deletion  
- Demonstrates understanding of resource lifecycle management  


<img width="auto" height="auto" alt="Screenshot (353)" src="https://github.com/user-attachments/assets/ce52e0be-5854-479e-bbaf-59c5708cb550" />

_**Attempted to delete the lock for Storage account**_

---

<img width="auto" height="auto" alt="Screenshot (354)" src="https://github.com/user-attachments/assets/dadbaf82-928a-4ac8-a848-6922e3680f13" />

_**Attempted to delete the lock for the resource group**_

---

<img width="auto" height="auto" alt="Screenshot (360)" src="https://github.com/user-attachments/assets/dff357b5-b19b-428c-9b66-0c478443479c" />

_**Attempted to delete the resource group to prevent Azure ongoing charges**_


---

## 💻 Azure CLI (Automation Example)

### 🔹 Resource Group Level Lock (Recommended)

```bash
# Create a ReadOnly lock on resource group
az lock create \
  --name ReadOnlyLock \
  --lock-type ReadOnly \
  --resource-group rg-gp-tags-locks

# List locks
az lock list --resource-group rg-gp-tags-locks

# Delete lock
az lock delete \
  --name ReadOnlyLock \
  --resource-group rg-gp-tags-locks

```

### 🔹 Resource-Level Lock (Storage Account Example)

```bash
# Create a CanNotDelete lock on a specific storage account
az lock create \
  --name NoDeleteLock \
  --lock-type CanNotDelete \
  --resource-group rg-gp-tags-locks \
  --resource-name olastorageaccount101 \
  --resource-type Microsoft.Storage/storageAccounts

# List locks
az lock list --resource-group rg-gp-tags-locks

# Delete lock
az lock delete \
  --name NoDeleteLock \
  --resource-group rg-gp-tags-locks \
  --resource-name olastorageaccount101 \
  --resource-type Microsoft.Storage/storageAccounts

```

## ✅ Project Outcome

* Implemented Azure governance controls to protect resources
* Prevented accidental deletion using control plane restrictions
* Demonstrated structured resource organization strategy
* Validated enforcement of cloud security and operational policies

## 🧠 Key Learnings

* Tags enable efficient resource management and cost tracking
* Locks provide critical protection in production environments
* Azure enforces governance at the control plane level
* Proper cleanup is essential for cost and resource optimization

## 🔐 Real-World Relevance

This project reflects responsibilities of:

* IT Support Engineers
* Cloud Support Engineers
* Azure Administrators

Including:

* Preventing outages caused by accidental deletions
* Enforcing governance policies
* Managing shared cloud environments securely


## 👨‍💻 Author

**Abeeb Olabode**

Aspiring IT Support / Cloud Engineer

## ⭐ Final Note

This project demonstrates hands-on experience with Azure governance, resource protection, and operational control using Microsoft Azure, showcasing practical skills required for real-world IT and cloud support roles.
