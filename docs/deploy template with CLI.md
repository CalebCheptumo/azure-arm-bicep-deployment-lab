# Task 4: Deploy a Template with the CLI

In this task, I used Azure Cloud Shell with the Azure CLI (Bash) to deploy a managed disk by uploading and editing a previously exported ARM template and parameters.

## Lab Context

- Resource group: `az104-rg3`
- Target: Managed disk, deployed using Azure CLI
- Files: `template.json`, `parameters.json` (from earlier export)

## Steps Completed

1. **Switch to Bash in Cloud Shell**  
   I switched the Cloud Shell environment to Bash to use the Azure CLI.  
   ![Switch to bash](../screenshots/Deploy%20a%20template%20with%20the%20CLI/switch%20to%20bash.png)

2. **Verify and open template/parameters**  
   I checked that the required JSON files (`template.json`, `parameters.json`) were present and opened them to confirm values.  
   ![Verify template and parameters json file](../screenshots/Deploy%20a%20template%20with%20the%20CLI/verify%20template%20and%20parameters%20json%20file.png)

3. **Edit disk name (optional)**  
   I edited the disk name in the parameters/template to `az104-disk4` to deploy a new resource.  
   ![Edit the diskname to az104 disk](../screenshots/Deploy%20a%20template%20with%20the%20CLI/edit%20the%20diskname%20to%20az104%20disk.png)

4. **Deploy the template using CLI**  
   I ran the deployment command, referencing my ARM template and parameters files:

```bash
az deployment group create --resource-group az104-rg3 --template-file template.json --parameters parameters.json
```

![Deploy](../screenshots/Deploy%20a%20template%20with%20the%20CLI/deploy.png)

5. **Confirm deployment**  
   Once the deployment succeeded, I ran a command to list all disks and confirmed the newly deployed resource.

```bash
az disk list --output table
```

![Confirm disk created](../screenshots/Deploy%20a%20template%20with%20the%20CLI/confirm%20disk%20created.png)

## Key Takeaways

- CLI-based deployments are efficient and scriptable for repeated resource provisioning.
- Always review and edit JSON template/parameter files before deployment.
- Validate deployment success by checking both Azure Portal and CLI output.
