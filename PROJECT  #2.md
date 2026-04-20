## ☁️ PROJECT 2: Standardizing VM Deployments Using Azure Custom Images & ARM Templates
### 🔍 Real-World Scenario

In enterprise environments, deploying virtual machines manually often leads to configuration inconsistencies, slower provisioning, and increased risk during system recovery.

This project simulates how an IT Support / Cloud Support professional can:

* Standardize VM deployments
* Reduce configuration errors
* Enable faster recovery during incidents

by creating a reusable Azure Custom Image and exporting an ARM template for consistent redeployment.

---

### 📌 Project Overview

This project demonstrates the process of:

* Generalizing an Azure Virtual Machine (VM)
* Capturing it as a reusable Custom Image
* Exporting the infrastructure as an ARM template

The focus is on preparing production-ready, reusable infrastructure, which is critical for:

* Disaster recovery
* Rapid provisioning
* Environment consistency

----

### 🎯 Project Objectives

* Deploy and configure an Azure Virtual Machine
* Remove machine-specific data via generalization
* Capture the VM as a reusable custom image
* Export infrastructure as an ARM template
* Validate readiness for future redeployment


---


## 🧱 Architecture Flow

```
Configured VM 
   ↓
Generalization (Deprovision)
   ↓
Deallocated VM
   ↓
Custom Image (Reusable)
   ↓
ARM Template Export
   ↓
Future Consistent Deployments

```


<img width="auto" height="auto" alt="Screenshot (14)-1" src="https://github.com/user-attachments/assets/9c89bd7c-9034-480e-9b5b-2175513c1189" />

_VM overview (running)_



<img width="auto" height="auto" alt="533642030-d1f7a003-7d10-47f2-b9ca-0ec89f773c96~4" src="https://github.com/user-attachments/assets/ee701eb6-aff2-49d5-8a26-ecdaeb0056d0" />

_Captured custom image (overview)_


<img width="auto" height="auto" alt="Screenshot (309)" src="https://github.com/user-attachments/assets/e021e441-3972-4b41-83e0-0a6d201e5027" />

_Azure resource flow showing VM ➡️ Image ➡️ Vnet_


---

### 🛠 Environment & Tools

* Cloud Platform: Microsoft Azure
* VM OS: Ubuntu Linux / Windows Server
* Image Type: Managed Image
* Tools: Azure Portal, Azure CLI, SSH
* Infrastructure Format: ARM Template

---

### 🧠 Skills Demonstrated

* Azure VM Lifecycle Management
* VM Generalization (Linux & Windows awareness)
* Custom Image Creation
* Infrastructure Standardization
* ARM Template Export & Review
* Troubleshooting Deployment Failures
* Documentation & Reproducibility


---


### 🚀 Implementation Breakdown (With Technical Reasoning)
### 🔹 Step 1: Create and Configure VM

**What was done:**

* Deployed a Linux VM in Azure
* Installed updates and required configurations
* Verified access via SSH

**🔍 Why this matters:**

* The VM becomes the baseline image state
* All installed software and configurations are preserved in the final image
* Ensures future deployments are pre-configured and consistent

**💥 If done poorly:**
All future VMs created from this image will inherit misconfigurations.


![Screenshot (160)~2](https://github.com/user-attachments/assets/008b998e-e58b-4bf3-b2da-84f429351551)

_Created and configured the VM (Running) which shows the OS details (Linux//Ubuntu)_

---

![Screenshot_20260105-120144](https://github.com/user-attachments/assets/d7620d0f-018a-43cf-873d-19adcabd0afc)

_Connecting through SSH Azure CLI_

---

![Screenshot_20260105-120508](https://github.com/user-attachments/assets/acb84045-d0e8-4e72-9f0b-b341c2bce9d4)

_Connected successfully on Azure CLI (SSH)_ 


---

### 🔹 Step 2: Generalize the VM

```bash
sudo waagent -deprovision+user

```

**What was done:**

Removed machine-specific data from the VM

**🔍 Why this matters:**

**Eliminates:**
* User accounts
* SSH keys/username & password
* System identifiers
* Converts VM into a template-ready state

**💥 What breaks if skipped:**

* Duplicate machine identities
* Security risks
* Deployment failures when reusing image


<img width="auto" height="auto" alt="Screenshot (184)" src="https://github.com/user-attachments/assets/46dded37-e46f-4ce3-bd4c-ff80c096f154" />

 _Then enter y command_

---

Then:
```bash
exit 
```

<img width="auto" height="auto" alt="Screenshot (185)" src="https://github.com/user-attachments/assets/866c436d-a49a-49c6-867e-48026061e198" />

_Azure CLI (overview)_


#### Pro Tip: In the case where the terminal don't display the confirmation of the generalization of the VM, it's crucial to login again after exit to confirm.
After entering your username and password or SSH key to login again and the terminal display:
 _permission denied, try again later._
This error simply it indicates that your VM has been generalized just as below:


<img width="auto" height="auto" alt="Screenshot (191)" src="https://github.com/user-attachments/assets/85b2b219-a63f-4b0a-9f2a-c076f75964d2" />

_The error message above simply indicates that our VM has been generalized for capturing_

**💡 Real Insight:**
The “permission denied” error after exit confirms successful generalization.

---


### 🔹 Step 3: Deallocate the VM

**What was done:**

* Stopped the VM and ensured status = Deallocated

**🔍 Why this matters:**

* Releases compute resources
* Ensures disk is in a stable, consistent state
* Required by Azure for successful image capture

**💥 What breaks if skipped:**

* Image capture fails
* Risk of incomplete or corrupted image

**From Azure Portal:**

Navigate to the VM

Click Stop → ensure status shows Deallocated

---

![Screenshot (187)~2](https://github.com/user-attachments/assets/85478aec-340f-49f7-b3cc-803594eaf432)

_VM status showing Stopped (Deallocated) in Azure Portal_

> ⚠️ Skipping this step will cause image capture to fail.

---

### 🔹 Step 4: Capture Custom Image

**What was done:**

Captured VM as a Managed Image

**🔍 Why this matters:**

Creates a reusable blueprint of the system
Enables:
* Rapid scaling
* Consistent deployments
* Reduced manual configuration

**💡 Real-world use case:**
Used to deploy identical servers across environments (e.g., production, staging)

1. Go to the VM → Capture
2. Select Image type: Managed image
3. Provide:
Image name
4. Confirm and create 


<img width="auto" height="auto" alt="Screenshot (14)-1" src="https://github.com/user-attachments/assets/9c89bd7c-9034-480e-9b5b-2175513c1189" />

_Click on Capture at the VM overview page at the top to create your image_

---


<img width="auto" height="auto" alt="533667291-cb96b71a-e379-422d-93b3-4df59ac7bada~2" src="https://github.com/user-attachments/assets/c05ca536-a625-4f5c-b159-591ed73004b1" />

_Clicked on managed disk and also clicked on automatically delete original VM_

---


<img width="auto" height="auto" alt="533661868-e6a7025b-65f8-44ea-a715-40ecc68d6cfd~2" src="https://github.com/user-attachments/assets/df4c279c-6431-40bc-b731-9bfddd3875a5" />

_Confirm and Create image (named: My-VM-Ubuntu-Custom-Image-20260101053248), then wait for deployment_

---


<img width="auto" height="auto" alt="533661841-aaaf46b9-50a8-4b3f-8ac6-fe5f1d543355~2" src="https://github.com/user-attachments/assets/e0addd2c-464f-4a38-b6ca-5ed548a89940" />

_Successfully deployed the captured imaged while automatically deleted the VM overview_

---

<img width="auto" height="auto" alt="533642030-d1f7a003-7d10-47f2-b9ca-0ec89f773c96~4" src="https://github.com/user-attachments/assets/ee701eb6-aff2-49d5-8a26-ecdaeb0056d0" />


_Custom Captured image (overview)_


✅ The VM is automatically deleted after capture (if selected).


---


### 🔹 Step 5: Export ARM Template

**What was done:**

Exported infrastructure as JSON template:
#### [ARM Template link](https://github.com/kingola9/Azure-IT-Support-Portfolio/tree/8458c122e39d46c25c0636af285d20868e30bae5/PROJECT%20%232%20ARM%20Template)


**🔍 Why this matters:**

Enables Infrastructure as Code (IaC)
Allows:
* Automated deployments
* Version control
* Reproducibility

**💥 Without this:**

Infrastructure must be recreated manually
Higher risk of inconsistency and errors


1. Navigate to the Resource Group containing the VM or Image
2. Select Export template
3. Review the generated ARM template
4. Download the template and parameters file


<img width="auto" height="auto" alt="533670671-553f67dc-f5e2-4a5c-a35c-d4257b1a05c6~3" src="https://github.com/user-attachments/assets/6c6c5d28-fb86-407f-87d3-d159d4e640a7" />

_Exported template and downloaded it._


🎉 The template can now be reused to redeploy infrastructure when needed.

#### [ARM Template link](https://github.com/kingola9/Azure-IT-Support-Portfolio/tree/8458c122e39d46c25c0636af285d20868e30bae5/PROJECT%20%232%20ARM%20Template)

---


### 🧪 Validation (What Was Verified & Why)
* ✅ VM confirmed in Generalized state → ensures safe cloning
* ✅ Custom image successfully created → validates capture process
* ✅ ARM template exported → confirms infrastructure portability
* ✅ Template reviewed → ensures correct configuration

---

### 🚨 Issues Encountered & Resolutions

**❌ OS Profile Error**

**Cause:** VM not generalized

✅ **Fix:**

* Recreated VM
* Ran deprovision command
* Re-captured image

  
**❌ OS Disk / Managed Disk Error**

**Cause:** Incorrect disk references or deleted dependencies

✅ **Fix:**

* Ensured managed disk usage
* Maintained correct resource dependencies
* Avoid deleting image resource group

---

### 📊 Impact & Business Value

This solution enables:

* ⚡ Faster provisioning using pre-configured images
* 🔁 Consistent infrastructure across environments
* 🛡 Reduced configuration errors
* 🚑 Faster recovery during system failures
* 📦 Scalable and reusable deployments


  ### 🔐 Best Practices Applied
* Always generalize before capturing images
* Use dedicated resource groups for images
* Avoid hard-coded values in templates
* Validate VM state before capture
* Document all processes for reproducibility

---

### 💼 IT Support & Cloud Relevance
**🧑‍💻 IT Support Perspective**
* Enables rapid system recovery
* Reduces recurring configuration issues
* Improves incident response efficiency

**☁️ Cloud Support Perspective**
* Supports scalable infrastructure deployment
* Enhances consistency across environments
* Simplifies troubleshooting and maintenance
  
### 📈 Key Takeaways
* Standardization is critical in cloud environments
* Small mistakes (e.g., skipping deallocation) can break workflows
* Troubleshooting requires both system-level and cloud-level understanding
* Documentation is essential for repeatability and collaboration

---

### 🔐 Best Practices Learned

* Always generalize before capturing
* Store custom images in a dedicated resource group
* Avoid hard-coded resource IDs
* Use images for consistency and faster deployments
* Document steps for reproducibility

---

### 💼 Portfolio Value

* This project demonstrates:
* Azure VM lifecycle management
* Image-based standardization
* Template-based infrastructure portability
* Preparation for disaster recovery and redeployment

---

### Ideal for showcasing:

✅ IT Support Engineer

✅ Cloud Support Associate

✅ Junior Cloud Engineer roles

---

### 🔗 How to Use This Project

✅ Fork or clone this repository

✅ Follow the steps to recreate the process

✅ Modify the VM configuration to suit your needs


---

### 📬 Author

#### Abeeb Olabode 
Aspiring Cloud / IT Support Professional


---

⭐ If you found this project helpful, feel free to star the repository!
