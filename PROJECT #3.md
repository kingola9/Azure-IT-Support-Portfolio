---

# PROJECT 3: 🌐 Deploy a Static Website with Azure Blob Storage

## 📌 Project Overview

This project demonstrates how to deploy a **fully functional, publicly accessible static website** using **Microsoft Azure Blob Storage,** eliminating the need for traditional web servers or virtual machines.

It highlights real-world cloud practices such as **cost-efficient hosting, resource configuration, and public content delivery,** aligned with IT Support and Cloud Administrator responsibilities.

---

## 🎯 Key Objectives

* Provision and configure a cloud storage service
* Enable static website hosting using Azure-native features
* Deploy and manage web assets (HTML/CSS)
* Validate public access via HTTP endpoint
* Perform live updates to production content
* Implement proper resource cleanup to control costs

---

## 🏗️ Architecture & How It Works

Azure Blob Storage static hosting works by serving files directly from a special container called:

```
$web
```

**When enabled:**

* Azure automatically generates a public HTTP endpoint
* Files in $web are served as web content
* No backend server (e.g., Apache, Nginx) is required

👉 **Key Insight:**
This is a serverless hosting model, meaning:

* No infrastructure management
* High availability handled by Azure
* Lower cost compared to VM-based hosting

## 🧰 Tools & Technologies

* ☁️ Microsoft Azure (Blob Storage, Storage Accounts)
* 📦 Azure Blob Storage ($web container)
* 💻 Azure Portal
* ⚙️ Azure CLI (for automation and deployment)
* 🌐 HTML5 / CSS3
* 🌍 HTTP/HTTPS Endpoints

---

## ⚙️ Deployment Process (With Technical Reasoning)
### 1️⃣ Create a Storage Account

**Configured a General-purpose v2 (GPv2) storage account with:**

* **Standard Performance** → Cost-effective for static workloads
* **Locally Redundant Storage (LRS)** → Chosen for:
    - Lower cost
    - Sufficient durability for non-critical workloads

**👉 Why not GRS?**

Geo-redundant storage adds cost and is typically used for mission-critical production systems.

    
<img width="auto" height="auto" alt="Screenshot (212)" src="https://github.com/user-attachments/assets/3ea87015-5114-4d49-b96a-21b9c7629c03" />

_**Creation of storage acccount setup**_

---

<img width="auto" height="auto" alt="Screenshot (213)" src="https://github.com/user-attachments/assets/6e17b48b-44a3-4262-94e9-f83cd30048e0" />

_**Setup review & Creation**_

---


<img width="auto" height="auto" alt="Screenshot (215)" src="https://github.com/user-attachments/assets/34c67cde-d450-4e9d-8d83-42959f36da48" />

_**Storage account successfully deployed**_

---

<img width="auto" height="auto" alt="Screenshot (217)" src="https://github.com/user-attachments/assets/8e49ca9f-8f5a-45b6-ab1e-b5cf32595a2a" />

_**Storage account overview**_






---

### 2. Enable Static Website Hosting

* Opened the Storage Account
* Enabled **Static Website** feature
* Configured:

  * Index document: [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/45a4b0b04b369cd3206d153952c19a320ff20a05/PROJECT%20%233%20folder/index.html) → Default landing page
  * Error document: [`404.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/c5721a4e3655fea00db9a9040285201c109b21b6/PROJECT%20%233%20folder/404.html) → custom error handling

**👉 What happens internally?**

Azure maps incoming HTTP requests to files in `$web`
If a file is missing → serves [`404.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/c5721a4e3655fea00db9a9040285201c109b21b6/PROJECT%20%233%20folder/404.html)


<img width="auto" height="auto" alt="Screenshot (218)" src="https://github.com/user-attachments/assets/e71df010-9e34-413d-bd2e-fd728600201c" />

_**Enabled static website from the storage account left menu**_

---


<img width="auto" height="auto" alt="Screenshot (219)" src="https://github.com/user-attachments/assets/3bcf23a6-6b6f-4684-a0f7-f74f7d4781e9" />

_**Entered the document file name `index.html` & `404.html`**_

---

<img width="auto" height="auto" alt="Screenshot (220)" src="https://github.com/user-attachments/assets/96b1df3f-2dfc-46a1-a74d-8771ce9f281d" />

_**Generated the primary endpoint to access web**_


---

### 3. Upload Website Content

* Navigated to the `$web` container
* Uploaded:

  * [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/45a4b0b04b369cd3206d153952c19a320ff20a05/PROJECT%20%233%20folder/index.html)
  * [`404.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/c5721a4e3655fea00db9a9040285201c109b21b6/PROJECT%20%233%20folder/404.html)


**👉 These files are now:**

* Publicly accessible
* Served via Azure’s storage endpoint



<img width="auto" height="auto" alt="Screenshot (224)" src="https://github.com/user-attachments/assets/d7875e32-87e0-46b8-88c2-1650fe32e637" />

_**Navigated to the container page from the storage account menu**_

---

<img width="auto" height="auto" alt="Screenshot (227)" src="https://github.com/user-attachments/assets/22cfeabf-eb83-419e-aebe-bfa8c9850b98" />

_**Selected the `web` container to upload the website files**_

---

<img width="auto" height="auto" alt="Screenshot (228)" src="https://github.com/user-attachments/assets/209bd312-28f0-4310-9493-573c93392b0e" />

_**Uploaded the two website files**_


---

### 4. Access the Website

* Used the provided  [primary endpoint URL](https://olastorageaccount10.z28.web.core.windows.net/)
* Verified the site was publicly accessible

**👉 What this means:**

* Azure exposes your storage as a web-accessible endpoint
* Requests are handled directly by Azure’s storage service


<img width="auto" height="auto" alt="Screenshot (223)" src="https://github.com/user-attachments/assets/cfcfc645-4cb8-4641-a981-d7c1bcb43595" />

_**Navigated back to the static website page to copy the [primary endpoint URL](https://olastorageaccount10.z28.web.core.windows.net/) to access the website**_

---

<img width="auto" height="auto" alt="Screenshot (234)" src="https://github.com/user-attachments/assets/583c7fb6-ac68-4ff1-8a67-f0a84407bf27" />

_**Verified the landing page webite was publicly accessible**_

---


<img width="auto" height="auto" alt="Screenshot (233)" src="https://github.com/user-attachments/assets/a7d0df4c-c48b-4702-aab9-8e9f4e9cc5ef" />

_**Verified the 404 Error page webite was publicly accessible**_

---

### 5. Update Website Content

* Edited the [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/7337f952610664c4c1fa79908eb984986fca0f31/PROJECT%20%233%20folder/updated.html) file locally
* Re-uploaded the updated version
* Refreshed the browser to confirm live changes

**👉 Result:**

* Changes reflected instantly (no server restart required)

**👉 This demonstrates:**

* Real-world **continuous deployment behavior** for static sites


<img width="auto" height="auto" alt="Screenshot (316)" src="https://github.com/user-attachments/assets/21bddce3-07a9-45f1-97d2-49f6b941fb41" />

_**Edited the  [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/7337f952610664c4c1fa79908eb984986fca0f31/PROJECT%20%233%20folder/updated.html) file locally and re-uploaded the updated version to rewrite the previous version 1**_

---

<img width="auto" height="auto" alt="Screenshot (318)" src="https://github.com/user-attachments/assets/6fa987a2-94c8-4739-8277-30153d54e3a5" />

_**Successfully re-uploaded and overwritten the previous version**_ 

---

<img width="auto" height="auto" alt="Screenshot (235)" src="https://github.com/user-attachments/assets/58b9f91b-ed06-47bb-bd52-5d3c856a8430" />

_**Refreshed the browser to confirm the live changes**_

---

### 6. Clean Up Resources

* Deleted the Storage Account
* Ensured no ongoing Azure charges

**👉 Why this matters:**

* Prevents unnecessary billing
* Shows awareness of **cloud cost management** (critical in real jobs)

<img width="auto" height="auto" alt="Screenshot (248)" src="https://github.com/user-attachments/assets/8a829ee0-2e01-426a-a657-90972d46922f" />

_**Successfully deleted the resource group that contains the storage account to avoid ongoing Azure charges**_


---


## 💻 Azure CLI (Automation Enhancement)

To demonstrate automation capability:

```bash
# Create resource group
az group create --name rg-gp-static-website --location francecentral

# Create storage account
az storage account create \
  --name olastorageaccount10 \
  --resource-group rg-gp-static-website \
  --location francecentral \
  --sku Standard_LRS

# Enable static website hosting
az storage blob service-properties update \
  --account-name olastorageaccount10 \
  --static-website \
  --index-document index.html \
  --404-document 404.html

```

**👉 Why this matters:**

* Shows ability to automate deployments
* Aligns with real-world DevOps and cloud admin workflows

  
## ✅ Project Outcome

* Deployed a serverless static website using Azure-native services
* Eliminated need for infrastructure (VMs, web servers)
* Demonstrated cost-efficient cloud hosting architecture
* Validated ability to configure, deploy, and manage cloud resources end-to-end

---

## 🧠 Key Learnings
* Azure Blob Storage can function as a lightweight web hosting platform
* Static hosting reduces complexity and operational overhead
* Cloud services enable instant content updates without downtime
* Resource lifecycle management is essential for cost control

---


## 🔐 Real-World Relevance

This project simulates real IT/Cloud responsibilities:

* Hosting company landing pages
* Supporting web-based applications
* Managing public access to cloud resources
* Troubleshooting deployment and access issues

## 🔗 Useful Resources

* [Azure Blob Storage Documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/?utm_source=chatgpt.com)
* [Static Website Hosting Guide](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website?utm_source=chatgpt.com)

---

## 🧑‍💻 Author

**Abeeb Olabode**

Aspiring IT Support / Cloud Engineer

---

## ⭐ Final Note

This project demonstrates practical cloud skills aligned with real-world IT and cloud support roles, showcasing the ability to deploy scalable, cost-effective solutions using **Microsoft Azure**.
