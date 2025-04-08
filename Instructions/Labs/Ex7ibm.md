# Exercise 3: Data Engineering Ingest Data in Fabric with Fabric Copilot

### Estimated Duration: 80 minutes

## Overview

In the exercise, you will create a simple data pipeline to bring in customer sales data. You are using the KiZAN Fabric Tenant - where we have Copilot enabled, demonstrate doing the same thing, but by using a new Data Flow Gen2 And leveraging the native integration of Copilot to use natural language to ingest and transform your data.

## Lab objectives

You will be able to complete the following tasks:

- Task 1: Create New - Dataflow Gen2
 
### Task 1: Create New - Dataflow Gen2

In this task, you will create a new **Dataflow Gen2** in Microsoft Fabric's Data Factory, utilizing Copilot's natural language capabilities to ingest and transform data efficiently.

1. Select your workspace **fabric-<inject key="DeploymentID" enableCopy="false"/> (1)** from the left panel.Then, click on **+ New Item (2)**, search for **Dataflow Gen2 (3)** in the search bar, and select **Dataflow Gen2 (4)**.

    ![](./Images/Updated/E3-T1-S1.png)

1. Click on **Data Engineering (1)** icon from the botton left corner, Select **Data Factory (2)** Object in the workspace.

    ![New dataflow.](./Images/f32.png)

1. In the home page for your workspace, select **Dataflow Gen2**. 

   ![New dataflow.](./Images/data-factorygen2.png)

1. After a few seconds, the Power Query editor for your new dataflow opens as shown here.

   ![New dataflow.](./Images/new-dataflow.png)

1. Select **Import from a Text/CSV file**.

   ![New dataflow.](./Images/f33.png)

1. On the **Connect to data source** page, create a new data source with the following settings:

    - Connection settings: Select **Link to file (1)**
    - File path or URL: `https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv` **(2)**
    - Connection: **Create new connection (3)**
    - data gateway: **(none) (4)**
    - Authentication kind: **Anonymous (5)**
    - Click on **Next (6)**.

      ![New dataflow.](./Images/29.png)

1. On **Preview file data** page, Click on **Create**.

   ![New dataflow.](./Images/30.png)

1. Click **Copilot** button on Ribbon. 

    ![New dataflow.](./Images/31.png)

1. To better illustrate all that Copilot is doing for you, let me expand the UI a little to see what's going on behind the scenes.

1. Expand **Query Settings** (these are the steps in the query that bring in the data)

1. **View menu**: Look for the option or menu labeled **View** in the toolbar or menu bar. Click on it to reveal a dropdown menu.

1. **Diagram View**: From the dropdown menu, select **Diagram View**. This will switch your view to a visual representation of your code.

1. **Script View**: Once you're in Script View, you should be able to see the M-Code that Copilot has generated. This is the underlying code representation of the actions or commands depicted in the Diagram View.

   ![New dataflow.](./Images/1.png)

1. Looking at the data… Notice the **Item** Column. This is really three different fields -- It contains a short **description of the item, a color and a size**.

   ![New dataflow.](./Images/f35.png)

1.	The fields are not consistently delimited (' ' and then ',')

1. Let's use Copilot to clean this up, click on **Prmptflow (1)** icon and select **Add a step that (2)**:

    ```
   	Add a step that
    ```
    ![New dataflow.](./Images/f36.png)

1. Type the following into Copilot **(1)**:
 
    ```
    In the Item column, remove the ','
    ```
 
1. The Item column now consistently has a delimiter of **' '**. **(2)**

   ![New dataflow.](./Images/f55.png)

1. Show the m-code and new query step that the copilot generated.
 
   ```
   Add a step that
   ```
   ![New dataflow.](./Images/3.png)

1. Type the following into Copilot. Three new fields are now created to replace the Item Column.
 
    ```
    Split the Item column on the ' ', creating three new fields called Description, Color and Size
    ```

   ![New dataflow.](./Images/f37.png)

1. Show the m-code and new query step that the copilot generated
 
   >**Note:** Copilot can do more than transform the table, we can actually change data as well.

1. Scenario: think Red bikes are going to be a big seller, so increase the quantity in Inventory
Call out that the quantities for all items are 1.
 
1. Add a step to the query:

   ```
   Add a step that
   ```
   ![New dataflow.](./Images/3.png)

1. Type the following into Copilot:
 
    ```
    Multiply the Quantity column by 10 for all rows where the Color column equals 'Red'. Make sure that the Color column is treated as text and the Quantity column as a number.
    ```
 
1. Show that the quantity field for Red bikes is now 10 instead of 1.

   ![New dataflow.](./Images/6.png)
 
1. Here is a concise summary highlighting the impacts of Visual Query and M-Query/M-Code scripting:

1. Close the Report.

1. **Visual Query**:
   - **Streamlines data exploration**: Visual Query tools offer intuitive interfaces, enabling users to interact with data visually, and facilitating quicker insights without extensive coding.
   - **Enhances accessibility**: With Visual Query, users with varying technical expertise can extract insights from data, reducing reliance on specialized programming skills and promoting broader data utilization across teams.

1. **M-Query/M-Code scripting**:
   - **Enables advanced data manipulation**: M-Query/M-Code scripting provides a robust framework for performing intricate data transformations and analysis, empowering users to tailor processes to specific requirements beyond the capabilities of visual tools.
   - **Facilitates automation and customization**: Through M-Query/M-Code scripting, users can automate repetitive tasks, build custom functions, and create tailored solutions, increasing efficiency and flexibility in data workflows.

### Summary

In this exercise, you learned how to ingest data into Microsoft Fabric using Fabric Copilot. The lab covered setting up data pipelines, automating data ingestion processes, and leveraging Fabric Copilot to streamline data operations. You practiced loading datasets into Fabric, explored different ingestion methods, and understood best practices for managing large-scale data workflows. By the end of the lab, you gained hands-on experience in efficient data ingestion within Fabric.

### Review
In this lab, you have completed:

  + Create New - Dataflow Gen2

### You have successfully completed the lab. Click on Next >> to procced with next Exercise.
