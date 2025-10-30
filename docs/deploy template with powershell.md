# Task 3: Configure the Cloud Shell and deploy a template with PowerShell

In this task, I used Azure Cloud Shell and PowerShell to deploy a managed disk using a previously exported ARM template and parameters. This demonstrates deploying infrastructure as code in a browser-based shell environment.

## Lab Context

- Resource group: `az104-rg3`
- Deployment method: PowerShell in Azure Cloud Shell
- Template files: `template.json` and `parameters.json`

## Steps Completed

1. **Open Azure Cloud Shell**  
From the Azure portal, I clicked the Cloud Shell icon to launch the browser-based shell environment.  
![Azure portal to access Cloud Shell](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/azure%20portal%20to%20access%20cloud%20shell.png)

2. **Switch to classic version (Cloud Shell)**  
I switched Cloud Shell to the classic experience to easily upload and manage files.  
![Switch to classic version](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/switch%20to%20classic%20version.png)

3. **Create the resource group**  
If not already present, I created the target resource group `az104-rg3`.  
![Create az104-rg3](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/create%20az104-rg3%20.png)

4. **Open the Cloud Shell Editor and upload template/parameter files**  
I used the editor (curly braces icon) to upload and open both `template.json` and `parameters.json`.  
![Open editor, edit template and parameters json](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/open%20editor%20edit%20template%20and%20parameters%20json.png)

5. **Edit template and parameters as needed**  
If necessary, I modified the templates (such as disk name or size) directly in the editor:  
- Template example:  
  ![Edit template json file](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/edit%20template%20json%20file.png)
- Parameters example:  
  ![Edit parameters json file](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/edit%20parameters%20json%20file.png)

6. **Deploy template using PowerShell**  
I ran the PowerShell deployment command, referencing my uploaded/existing template and parameters files:
```powershell
New-AzResourceGroupDeployment -ResourceGroupName az104-rg3 -TemplateFile template.json -TemplateParameterFile parameters.json
```
![Deploy to az104-rg3](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/deploy%20to%20az104-rg3.png)

7. **Confirm deployment**  
Once the deployment completed, I ran verification commands such as below to list disks and confirm successful provisioning:
```powershell
Get-AzDisk | Format-Table
```
![Confirm disk created](../screenshots/Configure%20the%20Cloud%20Shell%20and%20deploy%20a%20template%20with%20PowerShell/confirm%20disk%20created.png)

## Key Takeaways

- Azure Cloud Shell provides a quick way to manage and deploy resources from anywhere.
- Deploying with PowerShell and parameterized ARM templates makes redeployment consistent and efficient.
- You can modify infrastructure before deployment—simply edit the `template.json`/`parameters.json` files in the Cloud Shell editor.
