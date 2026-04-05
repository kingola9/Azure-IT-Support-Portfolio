#### *PROJECT 1*: *AZURE VIRTUAL MACHINE DEPLOYMENT & TROUBLESHOOTING*

#### **Project Overview 📌**

This project demonstrates hands-on experience deploying, configuring, and troubleshooting Linux virtual machines on Microsoft Azure.
It reflects real-world IT Support / Cloud Support responsibilities such as VM provisioning, authentication configuration, deployment issue resolution, and cost optimization using Azure CLI.

🧑‍💻 **Role:** 
_IT Support/Cloud Support_

#### ☁️  Environment & Tools: 

💡**Cloud Platform: Microsoft Azure**

💡**Operating System: Ubuntu 22.04 LTS**

💡**Deployment Methods: Azure Portal, ARM Templates**

💡**Command Line: Azure CLI**

💡**Authentication: SSH Keys, Username & Password**

## 🔧 Hands-on Tasks Performed (What I Did)

1️⃣ **Virtual Machine Deployment**

Deployed Linux (Ubuntu 22.04 LTS) Virtual Machines using:
* Azure Portal (GUI)
* ARM Templates (Infrastructure as Code)
* Selected VM sizes, regions, networking, and storage configurations.


2️⃣ **Authentication Configuration**

Configured VM access using:
* SSH public/private key authentication
* Username and password login
* Validated secure remote access to Linux VMs.

3️⃣ **Troubleshooting & Issue Resolution:**

Resolved common Azure VM deployment and access issues, including:

❌ Managed OS disk reference errors

❌ OSProfile misconfiguration issues

❌ Authentication errors:

* Permission denied (publickey)

* Password authentication failures

* Verified Azure resource provider settings and template dependencies.

4️⃣ **VM Monitoring & Management (Azure CLI)**
Checked VM runtime states:
* Running
* Stopped
* Deallocated
* Started and stopped virtual machines using Azure CLI commands to:
* Optimize cloud costs
* Control availability during testing


![531667842-9da55384-6751-45ec-b0ad-4c1483e46979~2](https://github.com/user-attachments/assets/6514c76c-a8f2-4df0-831e-c9e57af46bb2)


*Creation of Linux VM in process while configuring the VM size, region, OS image, OS Disk, Networking and storage configurations before deployment*

![531667841-ac131fb6-65c9-42bf-8c89-9839f0bcc888~2](https://github.com/user-attachments/assets/bbfa7fc4-1799-4b4f-b296-77252b8d8c89)

*Linux VM is in deployment in progress*

![531668820-fdff24b0-be1a-4e3e-a184-fe36f6ee096a~2](https://github.com/user-attachments/assets/8b6b9e78-a47a-43b2-ab8e-023ca373fe7a)

*Linux VM (Ubuntu 22.04 LTS) Successfully deployed*

![531667839-31f572c3-e69c-45a5-96e8-7b78b91a37bc~2](https://github.com/user-attachments/assets/91d721ca-44e2-426d-b773-2e00fd9e782a)

*Linux VM overview (running) after deployment*

![531667838-0e6ca802-29d9-44b7-aa40-6d93d8157ef5~2](https://github.com/user-attachments/assets/4cfb4d5e-6acd-429a-86ab-6619ae0ef4a4)

*Successfully connected to the (SSH) Azure CLI terminal (bash)*

![531668933-233aef51-ba94-4ea9-a4b3-65590b3c420b~2](https://github.com/user-attachments/assets/1b47cc13-0eef-4704-9eb7-e9977e134714)

*Resources in the Resource group (named: IntroAzureRG)*

![531669142-98da3ca0-ac9a-4ef4-97e9-2bdc68f142b8~2](https://github.com/user-attachments/assets/0e29a351-daca-4c3a-896f-7005a6b4dcb1)

*All resources in the Resource Manager*

![531669219-4d85cee0-4b4d-4348-b5b2-5cf67b683d9d~2](https://github.com/user-attachments/assets/813fd83f-f942-40c8-ab1e-1fee0dc2766b)

*Successfully Shutdown the VM and deallocated from the Azure CLI after checking the memory usage, running time, disk usage, creating of folder and creating of text file*

![531669484-c7a929ee-013b-4f04-996c-deaf6babda52~2](https://github.com/user-attachments/assets/ba9c1cd6-887d-4015-b27b-fb46ac3f0e92)

*Activity Log*

![531669519-fd8c926f-cb27-4124-a404-f8e67b67d934~2](https://github.com/user-attachments/assets/58035c18-df95-41ad-9c3f-8cec90d21158)

*Successfully monitored the VM and managed cost from heavy running OS disk while optimizing cloud cost*



🛠 **Skills Demonstrated:**
* Microsoft Azure Virtual Machines
* Linux Administration (Ubuntu)
* Azure CLI Operations
* ARM Template Troubleshooting
* Cloud Infrastructure Support
* IT Support & Problem Solving

####  🎥Video Demonstration of how i successfully deployed a Linux VM🔗:
#### ARM Template (JSON file): https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/d6a6b15ef0a51fbd976661008dda731149173094/template.json
