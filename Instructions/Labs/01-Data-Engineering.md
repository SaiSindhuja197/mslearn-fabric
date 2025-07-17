# Exercise 2: Ingest data with a pipeline in Microsoft Fabric

### Estimated Duration: 90 minutes

A data lakehouse is a common analytical data store for cloud-scale analytics solutions. One of the core tasks of a data engineer is to implement and manage the ingestion of data from multiple operational data sources into the lakehouse. In Microsoft Fabric, you can implement *extract, transform, and load* (ETL) or *extract, load, and transform* (ELT) solutions for data ingestion through the creation of *pipelines*.

Fabric also supports Apache Spark, enabling you to write and run code to process data at scale. By combining the pipeline and Spark capabilities in Fabric, you can implement complex data ingestion logic that copies data from external sources into the OneLake storage on which the lakehouse is based and then uses Spark code to perform custom data transformations before loading it into tables for analysis.

## Lab objectives

You will be able to complete the following tasks:

- Task 1: Sign up for Microsoft Fabric Trial
- Task 2: Create a workspace
- Task 3: Enable Copilot inside a Codespace
- Task 4: Explore shortcuts
- Task 5: Create a pipeline
- Task 6: Create a notebook
- Task 7: Use SQL to query tables
- Task 8: Create a visual query
- Task 9: Create a report

### Task 1: Sign up for Microsoft Fabric Trial

In this task, you will initiate your 60-day free trial of Microsoft Fabric by signing up through the Fabric app, providing access to its comprehensive suite of data integration, analytics, and visualization tools

1. On the **Power BI homepage**, click on the **Profile icon (1)** on the top right, and then click on **Free trial (2)**.

     ![Account-manager-start](./Images/f1.png)

1. A new prompt will appear asking you to **Activate your 60-day free Fabric trial capacity**, click on **Activate**.

      ![Account-manager-start](./Images/fabric-3.png)

1. Click on **Stay on current page** when prompted.

      ![Account-manager-start](./Images/fabric-2.png)

1. Now, open **Account manager (1)** again, and verify **Trial Status (2)**.

      ![Account-manager-start](./Images/lab1-image5.png)
      
### Task 2: Create a workspace

Here, you create a Fabric workspace. The workspace contains all the items needed for this lakehouse tutorial, which includes lakehouse, dataflows, Data Factory pipelines, notebooks, Power BI datasets, and reports.

1. On the left pane of the screen, select **Workspaces (1)** and then click on **+ New workspace (2)**.
pop-up
    ![New Workspace](./Images/f2.png)

1. Enter the detailsin the  **Create a workspace** form with the following details:
 
   - **Name:** Enter **fabric-<inject key="DeploymentID" enableCopy="false"/>**
 
      ![name-and-desc-of-workspc](./Images/f3.png)
 
   - Under the **Advanced:** drop-down, Under **License mode**, select **Fabric capacity (1)**, and under **Capacity** Select available **fabric<inject key="DeploymentID" enableCopy="false"/> - <inject key="Region"></inject>(2)**, leave everything else as default and click on **Apply (3)** to create and open the new workspace.
 
      ![advanced-and-apply](./Images/f4.png)

### Task 3: Create a Lakehouse

Large-scale data analytics solutions have traditionally been built around a *data warehouse*, in which data is stored in relational tables and queried using SQL. The growth in "big data" (characterized by high *volumes*, *variety*, and *velocity* of new data assets) together with the availability of low-cost storage and cloud-scale distributed computing technologies has led to an alternative approach to analytical data storage; the *data lake*. In a data lake, data is stored as files without imposing a fixed schema for storage. Increasingly, data engineers and analysts seek to benefit from the best features of both of these approaches by combining them in a *data lakehouse*; in which data is stored in files in a data lake and a relational schema is applied to them as a metadata layer so that they can be queried using traditional SQL semantics.

In Microsoft Fabric, a lakehouse provides highly scalable file storage in a *OneLake* store (built on Azure Data Lake Store Gen2) with a metastore for relational objects such as tables and views based on the open source *Delta Lake* table format. Delta Lake enables you to define a schema of tables in your lakehouse that you can query using SQL.

Now that you have created a workspace in the previous step, it's time to switch to the *Data engineering* experience in the portal and create a data lakehouse into which you will ingest data.

1. At the bottom left of the Power BI portal, select the **Power BI (1)** icon and switch to the **Fabric (2)** experience.

   ![](./Images/E2T1S1.png)

   ![](./Images/E1T1S1-1.png)
   
1. In the left pane, navigate to your Workspace named as **fabric-<inject key="DeploymentID" enableCopy="false"/> (1)**, click on **+ New item (2)** to create a new lakehouse.

    ![](./Images/Lake2.png)

1. In the search box, search for **Lakehouse (1)** and select **Lakehouse (2)** from the list.

    ![](./Images/Lake1.png)

1. Enter the **Name** as **Lakehouse_<inject key="DeploymentID" enableCopy="false"/> (1)** and Click on **Create (2)**.

    ![](./Images/Lake3.png)

    >**Note:** After a minute or so, a new lakehouse with no **Tables** or **Files** will be created.

1. On the **Lakehouse_<inject key="DeploymentID" enableCopy="false"/>** tab in the pane on the left, click the **Ellipsis(...)** menu for the **Files (1)** node, click on **New subfolder (2)**.
    
    ![](./Images/lake4.png)

1. Create a subfolder named **new_data (1)** and click on **Create (2)**.

    ![](./Images/Lake5.png)

### Task 4: Explore shortcuts

In many scenarios, the data you need to work within your lakehouse may be stored in some other location. While there are many ways to ingest data into the OneLake storage for your lakehouse, another option is to instead create a *shortcut*. Shortcuts enable you to include externally sourced data in your analytics solution without the overhead and risk of data inconsistency associated with copying it.

1. In the **Ellipsis(...) (1)** menu for the **Files** folder, select **New shortcut (2)**.

   ![02](./Images/Lake6.png)

1. View the available data source types for shortcuts. Then close the **New shortcut** dialog box without creating a shortcut.

   ![](./Images/Lake7.png)

### Task 5: Create a pipeline

In this task, you will create a pipeline to automate data processing workflows. You’ll define the sequence of data transformation steps, configure the necessary components, and set up triggers for execution. This will streamline your data integration processes and improve efficiency in handling data tasks. A simple way to ingest data is to use a **Copy data** activity in a pipeline to extract the data from a source and copy it to a file in the lakehouse.

1. In the left pane, navigate back to the workspace **fabric-<inject key="DeploymentID" enableCopy="false"/> (1)**, then click on **+ New item (2)** and then select **Data pipeline (3)**.

    ![](./Images/Lake2.png)

1. In the search box, search for **Data pipeline (1)** and select **Data pipeline (2)** from the list.

    ![](./Images/Lake8.png)

1. Create a new data pipeline named **Ingest Sales Data Pipeline (1)** and click on **Create (2)**. 
    
    ![](./Images/Lake9.png)
   
1. If the **Copy data** wizard doesn't open automatically, select **Copy data assistant (1)** in the pipeline editor page.

   ![03](./Images/E2-T3-S3.png)

1. In the **Copy Data** wizard, on the **Choose a data source** page, search for **Http (1)** and select **Http (2)** source.

   ![](./Images/Lake10.png)

1. In the **Connection settings** pane, enter the following settings for the connection to your data source:
    
    - URL: **`https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv` (1)**
    - Connection: **Create new connection (2)**
    - Connection name: **Connection<inject key="DeploymentID" enableCopy="false"/> (3)**
    - Authentication kind : **Anonymous (4)**
    - Click on **Next (5)**
  
   ![](./Images/Lake11.png)
    
1. Make sure the following settings are selected:
    
    - Relative URL: **Leave blank**
    - Request method: **GET**
    - Additional headers: **Leave blank**
    - Binary copy: **Unselected**
    - Request timeout: **Leave blank**
    - Max concurrent connections: **Leave blank**
    - Click on **Next**
    
    ![05](./Images/Lake12.png)
   
1. Wait for the data to be sampled and then ensure that the following settings are selected:
    
    - File format: **DelimitedText (1)**
    - Column delimiter: **Comma (,) (2)**
    - Row delimiter: **Line feed (\n) (3)**
    - Select **Preview data (4)** to see a sample of the data that will be ingested.
    - Observe the sample of the data that will be ingested. Then close the data preview and click on **Next**.
    
    ![Account-manager-start](./Images/lab1-image12.png)
    ![Account-manager-start](./Images/lab1-image13.png)

1. On the **Choose data destination** page, click on **OneLake catalog (1)** and select the lakehouse **Lakehouse_<inject key="DeploymentID" enableCopy="false"/> (2)**.
    
    ![](./Images/Lake13.png)

1. Set the following data destination options.

    - Root folder: **Files (1)**
    - Folder path: **new_data (2)**
    - File name: **sales.csv  (3)**
    -  Click **Next (4)**:
   
    ![08](./Images/Lake14.png)

1. Set the following file format options and then select **Next (4)**:

    - File format: **DelimitedText (1)**
    - Column delimiter: **Comma (,) (2)**
    - Row delimiter: **Line feed (\n) (3)**
    - Click **Next (4)**:
   
    ![09](./Images/Lake15.png)

1. On the **Copy summary** page, review the details of your copy operation and then select **Save + Run**.

    ![09](./Images/Lake16.png)

1. A new pipeline containing a **Copy data** activity is created, as shown here:

    ![Screenshot of a pipeline with a Copy Data activity.](./Images/E1T3S13.png)

1. When the pipeline starts to run, you can monitor its status in the **Output** pane under the pipeline designer. Use the **&#8635;** (*Refresh*) icon to refresh the status, and wait until it has succeeded.

    ![Screenshot of a pipeline with a Copy Data activity.](./Images/01/Pg3-CpyOutput.png)

1. In the left pane, click on the **Lakehouse_<inject key="DeploymentID" enableCopy="false"/> (1)** page, expand **Files (1)** and select the **new_data (2)** folder, refresh the page and verify that the **sales.csv (3)** file has been copied.

    ![Account-manager-start](./Images/lab1-image16.png)

### Task 6: Create a notebook

In this task, you will create a notebook to document your data analysis process. You’ll set up the notebook environment, import necessary libraries, and structure your code to include data exploration, visualization, and insights. This will help you organize your workflow and enhance reproducibility in your analysis.

1. From the left pane, select the workspace named **Fabric-<inject key="DeploymentID" enableCopy="false"/>**.

    ![](./Images/E2-T4-S1.png) 

1. In the workspace, click on **+ New Item (1)**. In the New Item panel, search for **Notebook (2)** and select **Notebook (3)**.

    ![](./Images/E2-T4-S2.png) 

1. After a few seconds, a new notebook containing a single *cell* will open. Notebooks are made up of one or more cells that can contain *code* or *markdown* (formatted text).

1.  Click **Add data items (1)** drow-down under explorer and select **Exiting data source (2)** from the drop-down.

    ![](./Images/E2-T4-S4.png)  

1. Select the lakehouse we created earlier **Lakehouse-<inject key="DeploymentID" enableCopy="false"/> (1)** and click **Continue (2)**.
 
    ![](./Images/Lake17.png) 

1. Select the existing cell in the notebook, which contains some simple code, and then replace the default code with the following variable declaration and click on **&#9655; Run**.

    ```python
   table_name = "sales"
    ```

   ![11](./Images/01/Pg3-Notebook-S2.png) 

1. In the **Ellipsis(...) (1)** menu for the cell (at its top-right) select **Toggle parameter cell (2)**. This configures the cell so that the variables declared in it are treated as parameters when running the notebook from a pipeline.

     ![Account-manager-start](./Images/Lake18.png)

1. Under the parameters cell, use the **+ Code** button to add a new code cell. 

     ![](./Images/E2-T4-S9.png) 

1. Add the following code to it:

    ```python
    from pyspark.sql.functions import *
    
    # Read the new sales data
    df = spark.read.format("csv").option("header","true").option("inferSchema","true").load("Files/new_data/*.csv")

    ## Add month and year columns
    df = df.withColumn("Year", year(col("OrderDate"))).withColumn("Month", month(col("OrderDate")))

    # Derive FirstName and LastName columns
    df = df.withColumn("FirstName", split(col("CustomerName"), " ").getItem(0)).withColumn("LastName", split(col("CustomerName"), " ").getItem(1))

    # Filter and reorder columns
    df = df["SalesOrderNumber", "SalesOrderLineNumber", "OrderDate", "Year", "Month", "FirstName", "LastName", "EmailAddress", "Item", "Quantity", "UnitPrice", "TaxAmount"]

    # Load the data into a managed table
    #Managed tables are tables for which both the schema metadata and the data files are managed by Fabric. The data files for the table are created in the Tables folder.
    df.write.format("delta").mode("append").saveAsTable(table_name)
    ```

     ![](./Images/code1.png) 

    This code loads the data from the sales.csv file that was ingested by the **Copy Data** activity, applies some transformation logic, and saves the transformed data as a **managed table** - appending the data if the table already exists.

1. Verify that your notebooks look similar to this, and then use the **&#9655; Run all** button on the toolbar to run all of the cells it contains.

    ![Screenshot of a notebook with a parameters cell and code to transform data.](./Images/fab8.png)

    > **Note**: Since this is the first time you've run any Spark code in this session, the Spark pool must be started. This means that the first cell can take a minute or so to complete.

1. (Optional) You can also create **external tables** for which the schema metadata is defined in the metastore for the lakehouse, but the data files are stored in an external location.

    ```python
    df.write.format("delta").saveAsTable("external_sales", path="<abfs_path>/external_sales")

    #In the Lakehouse explorer pane, in the ... menu for the Files folder, select Copy ABFS path.

    #The ABFS path is the fully qualified path to the Files folder in the OneLake storage for your lakehouse - similar to this:

    #abfss://workspace@tenant-onelake.dfs.fabric.microsoft.com/lakehousename.Lakehouse/Files
    ```
    > **Note**: To run the above code, you need to replace the <abfs_path> with your abfs path


1. When the notebook run has completed, click on your  **Lakehouse** pane on the left, in the **Ellipsis(...)** menu for **Tables** select **Refresh** and verify that a **sales** table has been created.

    ![.](./Images/fab-6.png)

1. Navigate back to the **Notebook** on the left pane and use the ⚙️ **Settings (1)** icon at the top to view the notebook settings. Then, set the **Name** of the notebook to **Load Sales Notebook (2)** and close the settings pane.

     ![.](./Images/fab-7.png)
 
1. In the hub menu bar on the left, select your lakehouse.  

    ![.](./Images/newfab-1.png)

1. In the **Explorer** pane, refresh the **view (1)**. Then expand **Tables (2)**, and select the **sales (3)** table to see a preview of the data it contains.

    ![.](./Images/newfab-2.png)

### Task 7: Use SQL to query tables

In this task, you will use SQL to query tables in a database. You'll write SQL statements to retrieve, filter, and manipulate data from specified tables, allowing you to analyze and extract meaningful insights from the dataset. This will enhance your understanding of data retrieval and improve your SQL skills.

1. At the top-right of the Lakehouse page, switch from **Lakehouse** to **SQL analytics endpoint**. Then wait a short time until the SQL query endpoint for your lakehouse opens in a visual interface from which you can query its tables, as shown here:

    ![.](./Images/Lake19.png)

1. Use the **New SQL query** button to open a new query editor, and enter the following SQL query:

    ![](./Images/E2-T5-S2.png)

    ```SQL
   SELECT Item, SUM(Quantity * UnitPrice) AS Revenue
   FROM sales
   GROUP BY Item
   ORDER BY Revenue DESC;
    ```

1. Use the **&#9655; Run** button to run the query and view the results, which should show the total revenue for each product.

    ![](./Images/E2-T5-S3.png)

### Task 8: Create a visual query

In this task, you will create a visual query in Power BI using Power Query. You’ll begin by adding the **sales** table to the query editor, select relevant columns, and apply a **Group by** transformation to count distinct line items for each sales order. Finally, you'll review the results to see the summarized data.

1. On the toolbar,under **New SQL query (1)** drop-down select **New visual query (2)**.

    ![](./Images/Lake20.png)

1. In the Lakehouse, navigate to **Schemas**, then to **dbo**, expand the **tables** folder and select the **sales** table. In the sales table click on **Elipsis &#8230; (1)** and select **Insert into canvas (2)** it in the new visual query editor pane that opens to create a Power Query. 

    ![](./Images/Lake21.png)

1. In the **Manage columns (1)** menu, select **Choose columns (2)**. Then select only the **SalesOrderNumber and SalesOrderLineNumber (3)** columns and click on **OK (4)**.

    ![Account-manager-start](./Images/lab1-image22.png)

    ![Account-manager-start](./Images/lab1-image23.png)

1. Click on **+ (1)**, in the **Transform table** menu, select **Group by (2)**.

    ![Screenshot of a Visual query with results.](./Images/Lake22.png)

1. Then group the data by using the following **Basic** settings.

    - Group by: **SalesOrderNumber (1)**
    - New column name: **LineItems (2)**
    - Operation: **Count distinct values (3)**
    - Column: **SalesOrderLineNumber (4)**
    - click **OK (5)**

        ![Screenshot of a Visual query with results.](./Images/01/Pg3-VisQuery-S4.01.png)

1. When you're done, the results pane under the visual query shows the number of line items for each sales order.

    ![Screenshot of a Visual query with results.](./Images/E2-T6-S6.png)

### Task 9: Create a report

In this task, you will create a report to visualize and present your data findings. You'll gather relevant data, select appropriate visualizations, and structure the report for clarity and insight. This process will help you effectively communicate your analysis and support data-driven decision-making.

1. At the top of the SQL analytics endpoint page, select the **Model Layouts** tab.
    
    ![](./Images/Lake23.png)

    >**Note:** You might notice some additional tables appeared as shown below, please ignore the system tables which are shown ignore.

    ![Screenshot of a data model.](./Images/ig.png)

    > **Note**: In this exercise, the data model consists of a single table. In a real-world scenario, you would likely create multiple tables in your lakehouse, each of which would be included in the model. You could then define relationships between these tables in the model.

1. In the top menu bar, select the **Reporting** tab. Then select **New report**.

    ![](./Images/E2-T7-S2.png)
   
1. In the pop-up, click on **Continue** for adding data to the default semantic model.

    ![](./Images/E2-T7-S3.png)

1. In the **Data** pane on the right, expand the **sales** table. Then select the following fields:

    - **Item (1)**

    - **Quantity (2)**

   Then, a **Table visualization (3)** is added to the report.

     ![Screenshot of a report containing a table.](./Images/E2-T7-S4.png)
   
1. Hide the **Data** and **Filters** panes to create more space if required. Then, make sure the **Table visualization is selected (1)** and in the **Visualizations** pane, change the visualization to a **Clustered bar chart (2)** and resize it as shown here.

      ![Screenshot of a report containing a clustered bar chart.](./Images/E2-T7-S5.png)

      ![Screenshot of a report containing a clustered bar chart.](./Images/E2-T7-S5a.png)

1. On the **File (1)** menu, select **Save As (2)**. Then, name the Report as **Item Sales Report (3)** and click **Save (4)** in the workspace you created previously.

      ![](./Images/Lake25.png)
      ![](./Images/Lake26.png)

1. In the hub menu bar on the left, select your workspace to verify that it contains the following items:
    - Your lakehouse.
    - The SQL endpoint for your lakehouse.
    - A default dataset for the tables in your lakehouse.
    - The **Item Sales Report** report.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
      
   - If you receive an InProgress message, you can hit refresh to see the final status.
   - If you receive a success message, you can proceed to the next task.
   - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

   <validation step="478b8d65-837a-4b29-b792-922fe3c10580" />

### Summary

In this exercise, you have created a Workspace, Lakehouse and imported data into it. You've seen how a lakehouse consists of files and tables stored in a OneLake data store. The managed tables can be queried using SQL and are included in a default dataset to support data visualizations.

### You have successfully completed the exercise. Click on Next >> to proceed with the next exercise.
