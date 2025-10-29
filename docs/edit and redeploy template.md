# Task 2: Edit an Azure Resource Manager template and redeploy the template

In this task, I used the template exported from a prior deployment to quickly redeploy a managed disk with changes. This shows how to iterate using ARM templates directly from the Azure portal.

## Lab Context

- Resource group: `az104-rg3`
- Starting point: Previously exported `template.json` and `parameters.json`
- Goal: Modify the template to deploy a new disk (for example, change name) and redeploy

## Steps Completed

1. **Azure portal | Deploy a custom template**
   From the portal search, I opened "Deploy a custom template" to start a custom deployment.
   ![Azure portal Deploy a custom template service](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/azure%20portal%20Deploy%20a%20custom%20template%20service.png)

2. **Custom deployment | Overview**
   I landed on the Custom deployment blade, which shows the deployment scope and options.
   ![Custom deployment overview blade](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/custom%20deployment%20overview%20blade.png)

3. **Template | Build your own template in the editor**
   I chose to build my own template in the editor to load and modify a local file.
   ![Edit template blade](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/edit%20template%20blade.png)

4. **Template editor | Load file**
   I clicked Load file and selected the exported `template.json` from local storage.
   ![Load template json file](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/load%20template%20json%20file.png)

5. **Template editor | Edit template.json**
   In the editor, I updated the disk name parameter/reference (for example, `az104-disk1` → `az104-disk2`) to deploy a new disk.
   ![Edit the template.json file](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/edit%20the%20template%20json%20file%20.png)

6. **Basics | Review inputs**
   I reviewed the Basics tab of the custom deployment to confirm subscription, resource group (`az104-rg3`), region, and parameter values.
   ![Review the Basics tab](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/review%20the%20basics%20tab.png)

7. **Review + create | Validate**
   I validated the deployment configuration and proceeded to Create.
   ![Review and create](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/review%20and%20create.png)

8. **Deployment | Your deployment is complete**
   The deployment completed successfully, confirming the template and parameters were valid.
   ![Deployment complete](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/deployment%20complete.png)

9. **Resource group | Overview**
   I returned to the resource group to confirm the newly deployed resource is present.
   ![az104-rg3 overview and resource](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/az104-rg3%20overview%20and%20resource.png)

10. **Resource group | Deployments**
    I opened the Deployments blade to verify the new deployment entry, status, and timestamps.
    ![Deployment blade confirm deployment list and status](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/deplyment%20blade%20confim%20deplyment%20list%20and%20status.png)

11. **Custom deployment | Inputs confirmation**
    I reviewed the Inputs page to confirm the disk name and parameter values used for this deployment.
    ![Input blade confirm disk name](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/input%20blade%20confirm%20disk%20name.png)

12. **Template | Review deployed template**
    I opened the Template blade for the deployment to review the exact `template.json` Azure used for this run.
    ![Template blade review deployed template](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/template%20blade%20review%20deployed%20template.png)

13. **Parameters | Review**
    I reviewed the Parameters tab that shows all parameter values bound during deployment.
    ![Parameters tab](../screenshots/edit%20and%20redeploy%20resource%20manager%20template/parameters%20tab.png)

## Key Verification

- The custom deployment completed successfully with the updated disk name.
- Resource group Deployments shows the new deployment with Succeeded status.
- Inputs confirm the parameter changes were applied.
- The deployment’s Template blade matches the edited `template.json`.

## Key Takeaways

- Loading and editing an exported ARM template streamlines repeatable deployments.
- Keep template and parameter names aligned (for example, `disk_name`) to avoid validation errors.
- Use the Deployments blade to audit inputs, templates, and outputs for every run.
