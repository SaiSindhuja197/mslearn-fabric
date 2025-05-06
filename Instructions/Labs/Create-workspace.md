# Exercise 1: Create a Fabric workspace

### Estimated Duration: 40 minutes

Microsoft Fabric lets you set up workspaces depending on your workflows and use cases. A workspace is where you can collaborate with others to create reports, notebooks, lakehouses, etc. This lab will introduce you to creating a workspace in Microsoft Fabric. You will learn how to set up a workspace, which serves as a collaborative environment for organizing and managing your projects, data, and resources.

## Lab objectives

You will be able to complete the following tasks:

- Task 1: Assign Fabric Administrator Role
- Task 2: Sign up for Microsoft Fabric Trial
- Task 3: Create a workspace
  
### Task 1: Assign Fabric Administrator Role

1. In the Azure portal, type **Microsoft Entra ID (1)** in the search box and select **Microsoft Entra ID (2)** from the results.

   ![Navigate-To-AAD](./Images/ws/entra01.png)

2. Navigate to **Roles and administrators (1)** under the **Manage** section.

   ![Roles-and-Administrator](./Images/E1-T1-S2.png)

3. In the **Roles and administrators** page, type **Fabric Administrator (1)** in the search box and select **Fabric Administrators (2)** from the results.

   ![search-fabric-admin](./Images/E1-T1-S3.png)

4. This will take you to the **Fabric Administrator | Assignments** page where you will have to assign yourself the **Fabric Administrator role**. Now, click on **+ Add assignments (1)**.

   ![click-add-assignments](./Images/E1-T1-S4.png)

5. Make sure to **check the box (1)** next to your username, confirm if it is **Selected (2)** and click on **Add (3)**.

   ![check-and-add-role](./Images/E1-T1-S5.png)

6. You can confirm the **Fabric Administrator** role has been added successfully by **Refresh (1)** Fabric Administrators | Assignments page. After **confirming (2)** it has been added successfully, navigate back to **Home (3)**.

   ![check-and-navigate-back-to-home](./Images/E1-T1-S6.png)

### Task 2: Sign up for Microsoft Fabric Trial

1. Copy the **Power BI homepage link**, and open this link inside the VM in a new tab.

   ```
   https://powerbi.com
   ```

   >**Note**: In case a sign-up page asks for a phone number, you can enter a dummy phone number to proceed.

2. Enter <inject key="AzureAdUserEmail"></inject> as the username/Email and <inject key="AzureAdUserPassword"></inject> as the password when prompted.

3. Select **Account manager (1)**, and click on **Free trial (2)**.

   ![Account-manager-start](./Images/E1-T2-S3.png)

4. A new prompt will appear asking you to **Activate your 60-day free Fabric trail Capacity**, click on **Activate**.

   ![Start-trial](./Images/E1-T2-S4.png)

5. Once successfully upgraded to a free Microsoft Fabric trial, you receive a confirmation message. Select **Stay on Current Page** to begin working in Fabric.

   ![Got-it](./Images/E1-T2-S5.png)

6. Now, open **Account manager (1)** again, and verify **Trial Status (2)**.

   ![Verify-trial-status](./Images/E1-T2-S6.png)

### Task 3: Create a workspace

Here, you create a Fabric workspace. The workspace contains all the items needed for this lakehouse tutorial, which includes lakehouse, dataflows, Data Factory pipelines, notebooks, Power BI datasets, and reports.

1.  Now, select **Workspaces** and click on **+ New workspace**.

    ![New Workspace](./Images/E1-T3-S1.png)

2. Fill out the **Create a workspace** form with the following details:

   - **Name:** Enter **Fabric-<inject key="DeploymentID" enableCopy="false"/>**

      ![name-and-desc-of-workspc](./Images/E1-T3-S2a.png)

   - **Advanced:** Expand it and Under **License mode**, select **Trial capacity (1)** and click on **Apply (2)** to create and open the workspace.

      ![advanced-and-apply](./Images/E1-T3-S2b.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
      
   - If you receive an InProgress message, you can hit refresh to see the final status.
   - If you receive a success message, you can proceed to the next task.
   - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

  <validation step="796cb471-1103-4bc8-8e98-9e6dd3e8c025" />

### Summary

In this exercise, you have assigned Fabric Administrator Role, signed up for the for Microsoft Fabric Trial and created a workspace

### You have successfully completed the lab
