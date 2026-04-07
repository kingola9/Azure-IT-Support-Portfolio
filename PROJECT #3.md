---

# PROJECT 3: 🌐 Deploy a Static Website with Azure Blob Storage

## 📌 Project Overview

This project demonstrates how to host a static website using **Microsoft Azure Blob Storage**. It walks through creating a storage account, enabling static website hosting, uploading HTML content, and updating it in real time.

The goal is to showcase hands-on cloud skills relevant to IT Support, Cloud, and DevOps roles.

---

## 🎯 Objectives

By completing this project, I was able to:

* Create and configure an Azure Storage Account
* Enable static website hosting
* Upload and manage website files (HTML, CSS)
* Access the website via a public endpoint
* Update live content
* Clean up resources to avoid unnecessary costs

---

## 🧰 Tools & Technologies

* ☁️ Microsoft Azure
* 📦 Azure Blob Storage
* 💻 Azure Portal
* 🌐 HTML/CSS

---

## 🚀 Deployment Steps

### 1. Create a Storage Account

* Navigated to **Microsoft Azure Portal**
* Created a new Storage Account with:

  * Standard performance
  * Locally-redundant storage (LRS)
  * General-purpose v2

    
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

  * Index document: [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/049512bf90af84ca3e2cb2cecf9e155c245424b5/PROJECT%20%233%20folder/index.html)
  * Error document: [`404.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/c5721a4e3655fea00db9a9040285201c109b21b6/PROJECT%20%233%20folder/404.html)


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

  * [`index.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/049512bf90af84ca3e2cb2cecf9e155c245424b5/PROJECT%20%233%20folder/index.html)
  * [`404.html`](https://github.com/kingola9/Azure-IT-Support-Portfolio/blob/c5721a4e3655fea00db9a9040285201c109b21b6/PROJECT%20%233%20folder/404.html)



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

* Used the provided **primary endpoint URL**
* Verified the site was publicly accessible


<img width="auto" height="auto" alt="Screenshot (223)" src="https://github.com/user-attachments/assets/cfcfc645-4cb8-4641-a981-d7c1bcb43595" />

_**Navigated back to the static website page to copy the primary endpoint URL to access the website**_

---

<img width="auto" height="auto" alt="Screenshot (234)" src="https://github.com/user-attachments/assets/583c7fb6-ac68-4ff1-8a67-f0a84407bf27" />

_**Verified the landing page webite was publicly accessible**_

---


<img width="auto" height="auto" alt="Screenshot (233)" src="https://github.com/user-attachments/assets/a7d0df4c-c48b-4702-aab9-8e9f4e9cc5ef" />

_**Verified the 404 Error page webite was publicly accessible**_

---

### 5. Update Website Content

* Edited the [`index.html`] file locally
* Re-uploaded the updated version
* Refreshed the browser to confirm live changes




---

### 6. Clean Up Resources

* Deleted the Storage Account
* Ensured no ongoing Azure charges

---

## ✅ Outcome

* Successfully deployed a fully functional static website
* Demonstrated ability to manage cloud storage and hosting
* Gained hands-on experience with real-world Azure workflows

---

## 📸 Sample Output

*(Add screenshots here of your Azure portal and hosted website)*

---

## 💡 Key Learnings

* Static websites can be hosted without a traditional web server
* Azure Blob Storage provides a cost-effective hosting solution
* Real-time updates are simple with file replacement
* Resource cleanup is essential in cloud environments

---

## 🔗 Useful Resources

* [Azure Blob Storage Documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/?utm_source=chatgpt.com)
* [Static Website Hosting Guide](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website?utm_source=chatgpt.com)

---

## 🧑‍💻 Author

**Abeeb Olabode**

Aspiring IT Support / Cloud Engineer

---

