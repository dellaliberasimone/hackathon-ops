# Operations Hackathon 🧑‍💻👩‍💻
Welcome to the Operations Hackathon. The goal is to develop an infrastructure described in the "Goal" section using the most modern development tools: Azure DevOps Repos/Pipeline for code and automation, GitHub Codespaces as development environment and obtaining assistance from GitHub Copilot.

## Prerequisites ✅
- Azure DevOps Repository
- Azure Resource Group
- Service Principal with Contributor Role in Resource Group for test/deploy
- Storage Account with a Blob contaienr in the Resource Group for the Terraform state

## Codespace Environment 💻
**Installed Software:** Terraform, Azure CLI  
**VS Code Extensions:** GitHub Copilot, Terraform, Azure

## Start the Hackathon 🏁
1) Replace <YOUR_ADO_REPO_CLONE_URL> and <YOUR_ENTRA_ID_TENANT_ID> placeholder in '.devcontainer/devcontainer.json' with the infomation of the repository in your Azure DevOps organization
2) Click on 'Code->New with options' and select a machine size to start the Codespace, wait for the inizialization and log-in to you Azure DevOps Tenant when prompted
3) Happy coding 😊

### Terraform Development 
Login to the Azure CLI interactively or using a Service Principal
```
az login -t <Tenant> --use-device-code 
az login -t <Tenant> --service-principal -u <app-id> -p <password-or-cert> --tenant <tenant>
```
or set the following variables:
```
export ARM_CLIENT_ID=<your-client-id>
export ARM_CLIENT_SECRET=<your-client-secret>
export ARM_TENANT_ID=<your-tenant-id>
export ARM_SUBSCRIPTION_ID=<your-subscription-id>
```
Execute terraform commands:
```
terraform init, validate, plan, apply
```

# Goal: Opticians App Infrastructure 🕶️
The infrustructure must be created by IaaC in Azure by using Terraform and a storage account for the state. The resources must be deployed in an existing resource group.

The reference architecture for the Azure Infrastructure is composed of:
1. Azure App Service: This is a fully managed platform for building, deploying, and scaling web apps. You can use it to host the web application. You can quickly build a web app using a language of your choice (e.g. C#, Python, JavaScript, TypeScript, Ruby, Go, and C++). In this case, the application would provide an interface for opticians to input customer data and prescription details.
2. Azure SQL Database: This is a fully managed relational database with built-in intelligence for high performance. You can use it to store the data collected from the app. The database would hold tables for customers and their respective prescription data.
3. Virtual Netowrk and Private Endpoint: The AppService must reach the the Azure SQL Database over a private network
4. Azure Front Door: The application muste be exposed for security and delivery purpose by an Azure Front Door

# GitHub Copilot assistance 🤖
Given the infrastructure requirments, try to ask to GitHub Copilot for help, following some suggestions:
<table>
	<tr><th>Requirements</th><th>Ask to GitHub Copilot…</th></tr>
	<tr>
		<td>The infrustructure must be created by IaaC in Azure  and a storage account must be used for the state.</td>
		<td>Generate Terraform file with azure provider and state on storage account</td>
  </tr>
	<tr>
		<td>
      The resources must be deployed in existing resource group.
		</td>
		<td>
		  Reference an existing resource group
		</td>
	</tr>
	<tr>
		<td>Azure App Service Resource
		</td>
		<td>
		1. Generate code for Azure App Service
		</td>
	</tr>
	<tr>
		<td>
		Azure SQL Database Resource
		</td>
		<td>
		1. Generate code for Azure SQL Database
		</td>
	</tr>
  <tr>
		<td>
		Virtual Netowrk and Private Endpoint
		</td>
		<td>
		1. Add a virtual network <br>
    2. Connect the App Service to the Azure SQL Database trough the virtual network
		</td>
	</tr>
   <tr>
		<td>
		Azure Front Door
		</td>
		<td>
		1. Add an Azure Front Door that exposes the Azure App Service
		</td>
	</tr>
</table>
