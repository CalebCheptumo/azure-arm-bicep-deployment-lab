# Task 5: Deploy a Resource by Using Azure Bicep

In this task, I used Azure Cloud Shell (Bash) and the Azure CLI to deploy a managed disk using an Azure Bicep template. Bicep provides concise, readable syntax for ARM deployments.

## Lab Context

- Resource group: `az104-rg3`
- Deployment tool: Azure CLI in Cloud Shell (Bash)
- Template file: `azuredeploydisk.bicep`

## Steps Completed

1. **Upload and edit the Bicep file**  
   I uploaded the `azuredeploydisk.bicep` file into Cloud Shell and opened the editor to set:

   - Disk name (e.g., `az104-disk5`)
   - SKU (e.g., `StandardSSD_LRS`)
   - Disk size (e.g., `32`)
     ![Upload and edit bicep file](../screenshots/Deploy%20a%20resource%20by%20using%20Azure%20Bicep/upload%20and%20edit%20bicep%20file.png)

2. **Deploy the Bicep template**  
   I ran the following CLI command to deploy the Bicep template:

```bash
az deployment group create --resource-group az104-rg3 --template-file azuredeploydisk.bicep
```

![Deploy the template](../screenshots/Deploy%20a%20resource%20by%20using%20Azure%20Bicep/deploy%20the%20template.png)

3. **Confirm the disk was created**  
   I confirmed successful deployment by checking the resource group in the portal and running:

```bash
az disk list --output table
```

![Confirm disk was created](../screenshots/Deploy%20a%20resource%20by%20using%20Azure%20Bicep/confirm%20disk%20was%20created.png)

## Key Takeaways

- Bicep streamlines template authoring for Azure deployments.
- You can iterate/test templates rapidly with Cloud Shell and the CLI.
- Validate deployment in both CLI and the Azure Portal.
