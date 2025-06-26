# Exercise 1: Create a Fabric workspace

### Estimated Duration: 40 Minutes

Microsoft Fabric lets you set up workspaces depending on your workflows and use cases. A workspace is where you can collaborate with others to create reports, notebooks, lakehouses, etc. This lab will introduce you to creating a workspace in Microsoft Fabric. You will learn how to set up a workspace, which serves as a collaborative environment for organizing and managing your projects, data, and resources.

## Lab objectives

You will be able to complete the following tasks:

- Task 1: Sign up for the Microsoft Fabric Trial
- Task 2: Create a workspace

### Task 1: Sign up for Microsoft Fabric Trial

In this task, you will initiate your 60-day free trial of Microsoft Fabric by signing up through the Fabric app, providing access to its comprehensive suite of data integration, analytics, and visualization tools

1. Copy the **Power BI homepage link**, and open this link inside the VM in a new tab.

   ```
   https://powerbi.com
   ```

   >**Note**: In case a sign-up page asks for a phone number, you can enter a dummy phone number to proceed.

1. Select **Account manager (1)**, and click on **Free trial (2)**.

     ![Account-manager-start](./Images/f1.png)

1. A new prompt will appear asking you to **Activate your 60-day free Fabric trial capacity**, click on **Activate**.

    ![image](https://github.com/user-attachments/assets/d12f89b8-955d-4e0c-b671-977c34e152d1)

    > **Note:** The trial capacity region may differ from the one shown in the screenshot. No need to worry – simply use the default selected region, activate it, and continue to the next step.  

1. Click on **Stay on current page** when prompted.

      ![Account-manager-start](./Images/fabric-2.png)

1. Now, open **Account manager (1)** again, and verify **Trial Status (2)**.

      ![Account-manager-start](./Images/lab1-image5.png)
      
### Task 2: Create a workspace

Here, you create a Fabric workspace. The workspace contains all the items needed for this lakehouse tutorial, which includes lakehouse, dataflows, Data Factory pipelines, notebooks, Power BI datasets, and reports.

1. Now, select **Workspaces (1)** and click on **+ New workspace (2)**.

    ![New Workspace](./Images/f2.png)

1. Fill out the **Create a workspace** form with the following details:
 
   - **Name:** Enter **fabric-<inject key="DeploymentID" enableCopy="false"/>**
 
      ![name-and-desc-of-workspc](./Images/f3.png)
 
   - **Advanced:** Expand it and Under **License mode**, select **Fabric capacity (1)**, Under **Capacity** Select available **fabric<inject key="DeploymentID" enableCopy="false"/> - <inject key="Region"></inject>(2)** and click on **Apply (3)** to create and open the workspace.
 
      ![advanced-and-apply](./Images/f4.png)

### Summary

In this exercise, you have signed up for the Microsoft Fabric Trial and created a workspace.

### You have successfully completed the exercise. Click on Next >> to proceed with the next exercise.
