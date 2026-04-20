## ☁️ PROJECT 5: Azure Serverless Project — HTTP Endpoint with Azure Functions

### 📌 Project Overview

This project demonstrates the deployment of a **serverless HTTP endpoint** using **Microsoft Azure Functions**, showcasing the ability to build and validate lightweight APIs without managing infrastructure.

The solution exposes a **publicly callable HTTP endpoint** that responds to requests (e.g., _“Hello World”_), while leveraging Azure’s built-in scalability, monitoring, and logging capabilities.

---

### 🌍 Real-World Scenario

This project simulates a **status-check API** for a web application.

In a production environment, companies use similar endpoints to:

* Check if a backend service is running (`/api/status`)
* Return application health metrics
* Integrate with monitoring tools or load balancers

**Example Use Case:**

A company hosting an e-commerce platform can use this endpoint to:

Allow monitoring systems to verify uptime
Trigger alerts if the API fails
Provide quick diagnostics for support engineers

**Why this matters:**

This transforms a simple “Hello World” function into a practical cloud support scenario, directly aligned with real IT and cloud job responsibilities.

---

### 🎯 Objectives

* Deploy a **Function Ap**p in Azure
* Create and deploy an **HTTP-triggered function** via Cloud Shell
* Test endpoint accessibility via browser/API call
* Monitor execution using built-in logs
* Apply clean-up to avoid unnecessary cloud costs

---

### 🧠 Key Skills Demonstrated
* Serverless architecture fundamentals
* CLI-based cloud deployment
* API endpoint creation and testing
* Monitoring and logging (Application Insights)
* Basic API security (access keys)
* Cost management

---

### ⚙️ Technologies Used
* Microsoft Azure
* Azure Functions
* Azure Cloud Shell
* Azure Application Insights
* Node.js (JavaScript runtime)
* Azure Functions Core Tools

### 🏗️ Architecture Overview

```
Client Request → HTTP Endpoint → Azure Function → Response Output
```

This architecture eliminates the need for:

* Virtual machines
* Server maintenance
* Manual scaling

---

### 🚀 Implementation Steps (With Technical Relevance)

### 1. Create Function App
* Provisioned a Function App in Azure
* Selected a consumption-based plan

**Why this matters:**

* Ensures auto-scaling and cost efficiency.

<img width="auto" height="auto" alt="Screenshot (373)" src="https://github.com/user-attachments/assets/e46869eb-38d9-45a8-a981-3bac23ccc81f" />

_**Creation of Function App Setup**__


----


<img width="auto" height="auto" alt="Screenshot (374)" src="https://github.com/user-attachments/assets/c9799a5c-1a2c-4ddc-bff2-ad2eefce09bb" />

_**Function App Deployment in Progress**_

---

<img width="auto" height="auto" alt="Screenshot (375)" src="https://github.com/user-attachments/assets/f5600a55-b9f0-450d-ac58-dfc21c55ab79" />

_**Function App Deployment successful & Overview**_

---

### 2. Create & Deploy HTTP Trigger Function (Cloud Shell)

**🔹 Task 1:** **Open Cloud Shell**

* Launched Azure Cloud Shell
* Selected Bash environment
* Initialized storage

**Validation:**  `$` prompt visible

**Why this matters:**

* Provides a ready-to-use CLI environment without local setup.


**🔹 Task 2**: **Create Function Project**

* **Created project folder:**
```
mkdir func-gp-endpoint && cd func-gp-endpoint
```

<img width="auto" height="auto" alt="Screenshot (376)" src="https://github.com/user-attachments/assets/bf9e1260-968e-43a6-93a9-66490ddfad5d" />

_**Created a project folder**_

---

* **Initialized project:**

```
func init --worker-runtime node --language javascript --model V4

```

<img width="auto" height="auto" alt="Screenshot (377)" src="https://github.com/user-attachments/assets/7fe8550b-8b86-4653-a846-a00f975908f7" />

_**Initialized project**_

---


* **Created HTTP trigger:**
```
func new --name GetStatus --template "HTTP trigger" --authlevel anonymous
````

<img width="auto" height="auto" alt="Screenshot (379)" src="https://github.com/user-attachments/assets/3fc0e319-154e-4054-81f7-3e43346d6e7a" />

_**Created a HTTP trigger**_

---

* **Verified file creation:**
```
ls src/functions/
```

<img width="auto" height="auto" alt="Screenshot (380)" src="https://github.com/user-attachments/assets/c89823cb-f4af-499c-b78b-43c4f41088ed" />

_**Verified file creation**_

**Validation:** `GetStatus.js` exists

**Why this matters:**

* HTTP trigger enables **API functionality**
* Anonymous access simplifies **initial testing**
* CLI workflow reflects **real-world DevOps practices**
  
**🔹 Task 3:** **Deploy Function to Azure**

* **Retrieved Function App name:**
```
FUNC_APP_NAME=$(az functionapp list --resource-group rg-gp-functions-endpoint --query "[0].name" -o tsv)
```

<img width="auto" height="auto" alt="Screenshot (381)" src="https://github.com/user-attachments/assets/2ba34a77-578d-4d28-b346-d334549e4e33" />

_**Retrieved Function App name**_

---

* **Published function:**
```
func azure functionapp publish $FUNC_APP_NAME
```

<img width="auto" height="auto" alt="Screenshot (382)" src="https://github.com/user-attachments/assets/c473e891-f736-4a63-a4ab-b22bac567c68" />

_**Published Function (Deployment in Progress)**_

---

* **Obtained public endpoint:**
```
https://func-gp-endpoint-ola-g6e8fddhfbd7bchy.francecentral-01.azurewebsites.net/api/getstatus
````

<img width="auto" height="auto" alt="Screenshot (394)" src="https://github.com/user-attachments/assets/998a12fb-35b8-4163-bcf8-e67fdae04beb" />

_**Function Deployment successful (Obtained public endpoint)**_


**Validation:** [Invoke URL](https://func-gp-endpoint-ola-g6e8fddhfbd7bchy.francecentral-01.azurewebsites.net/api/getstatus) generated

**Why this matters:**

* Transforms local code into a live cloud service.


---

### 3. Test Endpoint & Validate Accessibility

**🔹 Test Public Endpoint**

* Opened endpoint in browser
* Verified response (Hello World)
* Tested in incognito mode

**Validation:** Works without authentication

**Why this matters:**

* Confirms availability and public access.

**🔹 Verify in Azure Portal**

* Confirmed GetStatus function exists in Function App

**Why this matters:**

* Ensures successful deployment and visibility.

---

### 4. Enable Monitoring, Secure Access & Review Logs
   
**🔹 Enable Monitoring**

* Enabled Azure Application Insights
* Configured Log Analytics workspace

**Why this matters:**

* Provides performance tracking and diagnostics.


---

#### 🔹 Restrict Access (Security)

* **Updated authorization level**:
```
sed -i "s/authLevel: 'anonymous'/authLevel: 'function'/" src/functions/GetStatus.js
```

* **Redeployed function:**
```
func azure functionapp publish $FUNC_APP_NAME
```

**Why this matters:**

* Secures endpoint using function-level authentication.

**🔹 Test Secured Endpoint**

* Access without key → 401 Unauthorized
* Retrieved function key
* Access with key:

```
https://<function-app>/api/getstatus?code=<function-key>
```

**Validation:**

* Fails without key
* Works with key

**Why this matters:**

* Demonstrates basic API protection.

**🔹 Review Invocation Logs**

* Accessed Invocations tab
* Verified logs (status, duration, timestamp)

**Key Insight:**

* Successful calls logged
* Unauthorized requests not logged

**Why this matters:**
* Shows ability to monitor and troubleshoot live systems.

---

### 5. Clean Up Resources

* Deleted resource group
* Removed monitoring resources

**Why this matters:**

* Prevents unnecessary cloud costs.




 ### 📊 Sample Output
 
 **JSON**
 
 ```JSON
{
  "message": "Hello, World."
}

```

### 🛡️ Best Practices Applied & Learned

### 🔐 Security

* Avoided using anonymous access in production scenarios
* Learned to implement function-level or managed identity authentication

**Impact:** Prevents unauthorized access to APIs

---

### 📈 Monitoring & Observability

* Used built-in logging to track executions
* Understood integration with Application Insights

**Impact:** Enables faster troubleshooting and performance monitoring

---

### 💰 Cost Optimization

* Used consumption plan (pay-per-execution)
* Cleaned up resources after testing

**Impact:** Prevents unnecessary cloud spending

---

### ⚙️ Deployment Efficiency

* Used CLI tools via Cloud Shell instead of manual portal steps

**Impact:** Improves automation and aligns with DevOps practices

---

### 🧱 Scalable Design

* Leveraged serverless architecture

**Impact**: Automatically handles traffic spikes without manual scaling

---

### 🔗 Project Value to Employers

This project proves the ability to:

* Deploy and manage real cloud infrastructure
* Build and expose live API endpoints
* Use CLI tools in a cloud environment
* Apply monitoring, security, and cost best practices

---

### 🎯 Relevant Roles:

* IT Support Engineer

* Cloud Support Associate

* Azure Administrator

---

### Author

**Abeeb Olabode**

IT Support / Cloud Professional
