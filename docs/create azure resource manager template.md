# Task 1: Create an Azure Resource Manager template

In this task, I created a managed disk in the Azure portal and exported its Azure Resource Manager (ARM) template and parameters. This shows how to capture a known-good configuration as reusable infrastructure-as-code.

## Lab Context

- Resource group: `az104-rg3`
- Resource: Managed disk (no source)
- Region: East US (example in screenshots; use your preferred region)
- Outputs: `template.json` and `parameters.json` via Export template

## Steps Completed

1. **Disk | Overview**
   I started by checking the Disk Overview to understand the current state and key properties (location, size, SKU/storage type, encryption). This helps confirm what I’m about to build and later validate against.
   ![Disk overview](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/disk%20overview.png)

2. **Create a managed disk | Basics (wizard opened)**
   I clicked Create from the Disks blade. The "Create a managed disk" wizard opened on the Basics tab with empty/default fields ready to configure (Subscription, Resource group, Disk name, Region, Availability zone, Security type, Source type).
   ![Create managed disk — Basics tab](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/create%20managed%20disk%20basics%20tab.png)

3. **Resource groups | Create resource group**
   Since I needed a target scope, I created the resource group `az104-rg3` directly from the picker. This ensures all related artifacts land in the same RG.
   ![Create resource group az104-rg3](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/create%20resource%20group%20az104-rg3.png)

4. **Basics — populated with required settings**
   I completed the Basics tab:

   - Subscription: selected my active subscription
   - Resource group: `az104-rg3`
   - Disk name: `az104-disk1`
   - Region: East US
   - Availability zone: No infrastructure redundancy required
   - Security type: Standard
   - Source type: None (creating an empty disk)
     ![Basics populated](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/create%20managed%20disk%20basics%20populated.png)

5. **Size — choose capacity and performance**
   On Size, I changed the storage type to Standard HDD (locally redundant) and selected 32 GiB. This keeps the lab simple and cost-effective.
   ![Select disk size](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/select%20disk%20size.png)

6. **Review + create — validate configuration**
   I reviewed all tabs (Basics, Size, Encryption, Networking, Advanced, Tags). The validation passed. I clicked Create to start the deployment.
   ![Review and create managed disk](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/review%20and%20create%20managed%20disk.png)

7. **Deployment | Your deployment is complete**
   After a short wait, the deployment succeeded. From here, I clicked Go to resource to open the disk.
   ![Disk deployment complete](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/disk%20deployment%20complete.png)

8. **Disk | Overview (post-deployment)**
   On the disk Overview, I verified the essentials: name `az104-disk1`, region, SKU/storage type (Standard HDD), and size 32 GiB. This confirms the deployed configuration matches what I selected.
   ![az104-disk1 overview](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/az104-disk1%20overview.png)

9. **Automation | Export template — ARM template**
   From the disk’s Automation section, I opened Export template and reviewed the ARM Template tab. This shows the `template.json` that defines the managed disk resource declaratively.
   ![Export template — ARM tab](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/export%20template%20arm%20tab.png)

10. **Automation | Export template — Parameters**
    I switched to the Parameters tab to examine the `parameters.json` schema. This file captures input values separately for reuse across environments.
    ![Export template — Parameters tab](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/export%20template%20parameters%20tab.png)

11. **Automation | Export template — Bicep**
    Finally, I viewed the Bicep tab to see the equivalent Bicep representation (when available), which compiles to the same ARM template.
    ![Export template — Bicep tab](../screenshots/Create%20an%20Azure%20Resource%20Manager%20template/export%20template%20bicep%20tab.png)

## Key Takeaways

- ARM templates and parameter files let you redeploy this configuration consistently across environments.
- The portal’s Export template feature bootstraps infrastructure-as-code from a working deployment.
- Bicep provides a concise authoring experience and compiles to standard ARM templates.
