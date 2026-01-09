## PROJECT 2 : Creation of Custom Image through Generalization of VM and Exporting of Template

## 📌 Project Overview

This project demonstrates hands-on experience creating a reusable Azure Custom Image by generalizing a Virtual Machine (VM) and exporting the deployment template for future redeployment.

The focus is on VM generalization, image creation, and template export only — not full redeployment — to show how standardized infrastructure can be prepared for reuse and disaster recovery.


---

## 🧠 Skills Demonstrated

Microsoft Azure Virtual Machines

VM Generalization (Linux & Windows)

Azure Custom Images

Managed Disks

Resource Group Management

Exporting ARM Templates

Azure Portal & Azure CLI

Infrastructure Documentation



---

## 🛠 Environment & Tools

Cloud Platform: Microsoft Azure

VM OS: Ubuntu Linux / Windows Server (generalizable)

Image Type: Managed Image

Deployment Method: Azure Portal & ARM-compatible image



---

## 🎯 Project Objective

Create and configure an Azure Virtual Machine

Generalize the VM to remove machine-specific data

Capture the VM as a Custom Image

Export the VM deployment template for reuse



---

## 🧩 Architecture Flow

1. Create & configure Azure VM


2. Deprovision / Generalize the VM


3. Stop (Deallocate) the VM


4. Capture VM as Custom Image


5. Export ARM template


![Screenshot (160)~2](https://github.com/user-attachments/assets/008b998e-e58b-4bf3-b2da-84f429351551)
_VM overview (running)_

![Screenshot_20260106-172617~3](https://github.com/user-attachments/assets/d1f7a003-7d10-47f2-b9ca-0ec89f773c96)
_Captured custom image (overview)_

<img width="auto" height="auto" alt="Screenshot (95)" src="https://github.com/user-attachments/assets/1394e38e-8391-4077-9c9a-6f6b5ea14e1d" />
_Azure resource flow showing VM ➡️ Image ➡️ Vnet_


---

## 🚀 Step-by-Step Implementation

## Step 1: Create and Configure the VM

Create a Virtual Machine in Azure

Install updates and required software

Confirm VM boots and runs correctly


📸 Screenshots to add:


![Screenshot (160)~2](https://github.com/user-attachments/assets/008b998e-e58b-4bf3-b2da-84f429351551)

_Created and configured the VM (Running) which shows the OS details (Linux//Ubuntu)_

![Screenshot_20260105-120144](https://github.com/user-attachments/assets/d7620d0f-018a-43cf-873d-19adcabd0afc)

_Connecting through SSH Azure CLI_

![Screenshot_20260105-120508](https://github.com/user-attachments/assets/acb84045-d0e8-4e72-9f0b-b341c2bce9d4)

_Connected successfully on Azure CLI (SSH)_ 




---

## Step 2: Generalize the VM

🔹 For Linux VM (Ubuntu)

Connect via SSH and run:

```bash
sudo waagent -deprovision+user
```

<img width="auto" height="auto" alt="Screenshot (184)" src="https://github.com/user-attachments/assets/46dded37-e46f-4ce3-bd4c-ff80c096f154" />

 _Then enter y command_

Then:
```bash
exit 
```

<img width="auto" height="auto" alt="Screenshot (185)" src="https://github.com/user-attachments/assets/866c436d-a49a-49c6-867e-48026061e198" />

_Azure CLI (overview)_

## Pro Tip: In the case where the terminal don't display the confirmation of the generalization of the VM, it's crucial to login again after exit to confirm.
After entering your username and password or SSH key to login again and the terminal display:
 _permission denied, try again later._
This error simply it indicates that your VM has been generalized just as below:

<img width="auto" height="auto" alt="Screenshot (191)" src="https://github.com/user-attachments/assets/85b2b219-a63f-4b0a-9f2a-c076f75964d2" />

_The error message above simply indicates that our VM has been generalized for capturing_


---

## Step 3: Stop (Deallocate) the VM

From Azure Portal:

Navigate to the VM

Click Stop → ensure status shows Deallocated

![Screenshot (187)~2](https://github.com/user-attachments/assets/85478aec-340f-49f7-b3cc-803594eaf432)

_VM status showing Stopped (Deallocated) in Azure Portal_


> ⚠️ Skipping this step will cause image capture to fail.



---

## Step 4: Create the Custom Image

1. Go to the VM → Capture


2. Select Image type: Managed image


3. Provide:

Image name

4. Confirm and create 

![Screenshot (160)~2](https://github.com/user-attachments/assets/1ab43416-e248-4509-994e-102495500119)

_Click on Capture at the VM overview page at the top to crear your image_


<img width="auto" height="auto" alt="Screenshot (85)" src="https://github.com/user-attachments/assets/cb96b71a-e379-422d-93b3-4df59ac7bada" />


_Clicked on managed disk and also clicked on automatically delete original VM_

<img width="auto" height="auto" alt="Screenshot (88)" src="https://github.com/user-attachments/assets/e6a7025b-65f8-44ea-a715-40ecc68d6cfd" />

_Confirm and Create image (named: My-VM-Ubuntu-Custom-Image-20260101053248), then wait for deployment_


![Screenshot_20260106-172405~2](https://github.com/user-attachments/assets/aaaf46b9-50a8-4b3f-8ac6-fe5f1d543355)

_Successfully deployed the captured imaged while automatically deleted the VM overview_

![Screenshot_20260106-172617~3](https://github.com/user-attachments/assets/934317f9-a92a-4e1f-a189-58d7784708d3)

_Custom Captured image (overview)_


Resource group (recommended: separate group for Custom Images)

✅ The VM is automatically deleted after capture (if selected).


---

## Step 5: Export the Deployment Template

1. Navigate to the Resource Group containing the VM or Image


2. Select Export template


3. Review the generated ARM template


4. Download the template and parameters file


<img width="auto" height="auto" alt="Screenshot (100)" src="https://github.com/user-attachments/assets/553f67dc-f5e2-4a5c-a35c-d4257b1a05c6" />

_Exported template and downloaded it._


🎉 The template can now be reused to redeploy infrastructure when needed.

## ARM Template : https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/74e209659ab28850caac58a080c3eb5442ce1dd1/template-1.json

---

## 🧪 Validation & Validation

Confirm custom image is successfully created

Verify VM shows Generalized state before capture

Confirm template file downloads successfully

Review template for required parameters


📸 Screenshots to add:

Custom Image listed under Images

Exported template files on local machine



---

## ❗ Common Issues & Fixes

## OS Profile Error

### Cause: 

VM was not generalized before capture

### Fix:

Recreate VM

Run waagent -deprovision+user (Linux) or Sysprep (Windows)

Capture again



---

## OS Disk / Managed Disk Error

### Cause: 

Disk was referenced incorrectly or deleted

### Fix:

Ensure disk exists

Use Managed Image, not unmanaged disk

Avoid deleting image resource group



---

## 🔐 Best Practices Learned

Always generalize before capturing

Store custom images in a dedicated resource group

Avoid hard-coded resource IDs

Use images for consistency and faster deployments

Document steps for reproducibility



---

📸 Screenshots & Evidence (Add Your Proof)

VM running before generalization

Deprovision command / Sysprep screen

Image creation success

New VM deployed from image


> Screenshots can be found in the /screenshots folder.




---

## 💼 Portfolio Value

This project demonstrates:

Azure VM lifecycle management

Image-based standardization

Template-based infrastructure portability

Preparation for disaster recovery and redeployment


## Ideal for showcasing:

IT Support Engineer

Cloud Support Associate

Junior Cloud Engineer roles



---

## 🔗 How to Use This Project

Fork or clone this repository

Follow the steps to recreate the process

Modify the VM configuration to suit your needs



---

## 📬 Author

### Abeeb Olabode 

### Aspiring Cloud / IT Support Professional


---

⭐ If you found this project helpful, feel free to star the repository!
