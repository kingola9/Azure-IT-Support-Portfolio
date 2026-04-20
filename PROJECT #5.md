## ☁️ PROJECT 5: Azure Serverless Project — HTTP Endpoint with Azure Functions

### 📌 Project Overview

This project demonstrates the deployment of a serverless HTTP endpoint using Microsoft Azure Functions, showcasing the ability to build and validate lightweight APIs without managing infrastructure.

The solution exposes a publicly callable HTTP endpoint that responds to requests (e.g., “Hello World”), while leveraging Azure’s built-in scalability, monitoring, and logging capabilities.

### 🌍 Real-World Scenario

This project simulates a status-check API for a web application.

In a production environment, companies use similar endpoints to:

Check if a backend service is running (/api/status)
Return application health metrics
Integrate with monitoring tools or load balancers

**Example Use Case:**
A company hosting an e-commerce platform can use this endpoint to:

Allow monitoring systems to verify uptime
Trigger alerts if the API fails
Provide quick diagnostics for support engineers

**Why this matters:**
This transforms a simple “Hello World” function into a practical cloud support scenario, directly aligned with real IT and cloud job responsibilities.

### 🎯 Objectives
* Deploy a Function App in Azure
* Create and deploy an HTTP-triggered function via Cloud Shell
* Test endpoint accessibility via browser/API call
* Monitor execution using built-in logs
* Apply clean-up to avoid unnecessary cloud costs

### 🧠 Key Skills Demonstrated
* Serverless architecture fundamentals
* CLI-based cloud deployment
* API endpoint creation and testing
* Monitoring and logging (Application Insights)
* Basic API security (access keys)
* Cost management


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


### 🚀 Implementation Steps (With Technical Relevance)
### STEP 1. Create Function App
* Provisioned a Function App in Azure
* Selected a consumption-based plan

**Why this matters:**
Ensures auto-scaling and cost efficiency.

### STEP 2. Create & Deploy HTTP Trigger Function (Cloud Shell)
**🔹 Task 1:** Open Cloud Shell
Launched Azure Cloud Shell
Selected Bash environment
Initialized storage

**Validation:**  '$' prompt visible

**Why this matters:**
Provides a ready-to-use CLI environment without local setup.


**🔹 Task 2**: Create Function Project
Created project folder:
```
bash
mkdir func-gp-endpoint && cd func-gp-endpoint
```
Initialized project:

```
bash
func init --worker-runtime node --language javascript --model V4

```

Created HTTP trigger:
```
bash
func new --name GetStatus --template "HTTP trigger" --authlevel anonymous
````

Verified file creation:
```
bash
ls src/functions/
```

**Validation:** GetStatus.js exists

**Why this matters:**

* HTTP trigger enables API functionality
* Anonymous access simplifies initial testing
* CLI workflow reflects real-world DevOps practices
  
**🔹 Task 3:** Deploy Function to Azure

Retrieved Function App name:
```
bash
FUNC_APP_NAME=$(az functionapp list --resource-group rg-gp-functions-endpoint --query "[0].name" -o tsv)
```
Published function:
func azure functionapp publish $FUNC_APP_NAME
Obtained public endpoint:
https://<function-app-name>.azurewebsites.net/api/getstatus

Validation: Invoke URL generated

Why this matters:
Transforms local code into a live cloud service.





3. Test Endpoint & Validate Accessibility
🔹 Test Public Endpoint
Opened endpoint in browser
Verified response (Hello World)
Tested in incognito mode

Validation: Works without authentication

Why this matters:
Confirms availability and public access.

🔹 Verify in Azure Portal
Confirmed GetStatus function exists in Function App

Why this matters:
Ensures successful deployment and visibility.

4. Enable Monitoring, Secure Access & Review Logs
🔹 Enable Monitoring
Enabled Azure Application Insights
Configured Log Analytics workspace

Why this matters:
Provides performance tracking and diagnostics.

🔹 Restrict Access (Security)
Updated authorization level:
sed -i "s/authLevel: 'anonymous'/authLevel: 'function'/" src/functions/GetStatus.js
Redeployed function:
func azure functionapp publish $FUNC_APP_NAME

Why this matters:
Secures endpoint using function-level authentication.

🔹 Test Secured Endpoint
Access without key → 401 Unauthorized
Retrieved function key
Access with key:
https://<function-app>/api/getstatus?code=<function-key>

Validation:

Fails without key
Works with key

Why this matters:
Demonstrates basic API protection.

🔹 Review Invocation Logs
Accessed Invocations tab
Verified logs (status, duration, timestamp)

Key Insight:

Successful calls logged
Unauthorized requests not logged

Why this matters:
Shows ability to monitor and troubleshoot live systems.

5. Clean Up Resources
Deleted resource group
Removed monitoring resources

Why this matters:
Prevents unnecessary cloud costs.
