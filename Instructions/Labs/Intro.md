# Cloud scale analytics with Microsoft Fabric

### Overall Estimated Duration: 8 hours

## Overview

A global e-commerce company uses Microsoft Fabric for cloud-scale analytics to handle and analyze vast amounts of customer transaction data. They set up data pipelines for continuous ingestion of transactional information, which is stored in a scalable data warehouse. Real-time analytics monitor live data streams for immediate insights, while Apache Spark performs complex analyses and machine learning on the data. Dataflows Gen2 are employed to clean and transform data, and interactive notebooks allow data scientists to explore and model data dynamically. This integrated approach enables the company to make real-time, data-driven decisions and optimize their strategies effectively.

Cloud Scale Analytics with Microsoft Fabric enables organizations to process, analyze, and gain insights from massive amounts of data efficiently and effectively.

## Objective

This lab is designed to equip participants with hands-on experience in creating a workspace to manage data, ingesting it via pipelines, analyzing it in a data warehouse, performing real-time analytics, training models using notebooks, leveraging Apache Spark for complex analysis, and designing advanced data transformations with Dataflow Gen2.

1. **Create a Fabric workspace:** This hands-on exercise aims to set up a centralized environment in Microsoft Fabric to manage and collaborate on data projects. Participants will establish a centralized platform for managing and collaborating on data projects.

1. **Ingest data with a pipeline in Microsoft Fabric:** This hands-on exercise aims to use data pipelines to import and prepare data for analysis within Microsoft Fabric. Participants will automate the import and preparation of data for subsequent analysis.

1. **Analyze data in a data warehouse:** This hands-on exercise aims to perform complex queries and insights on large datasets stored in a data warehouse within Microsoft Fabric. Participants will execute complex queries to derive insights from large datasets.

1. **Get started with Real-Time Analytics in Microsoft Fabric:** This hands-on exercise aims to implement real-time data processing and analytics to gain immediate insights from live data streams. Participants will enable immediate insights and decision-making from live data streams.

1. **Use notebooks to train a model in Microsoft Fabric:** This hands-on exercise aims to utilize interactive notebooks for developing, training, and testing machine learning models within Microsoft Fabric. Participants will develop and refine machine learning models interactively.

1. **Analyze data with Apache Spark:** This hands-on exercise aims to leverage Apache Spark’s distributed computing capabilities to perform large-scale data analysis in Microsoft Fabric. Participants will perform scalable, high-performance data analysis on large volumes of data.

1. **Create a Dataflow (Gen2) in Microsoft Fabric:** This hands-on exercise aims to design and implement advanced data transformation workflows using Dataflow Gen2 for enhanced data integration and processing. Participants will design and execute sophisticated data transformation processes for integration and processing.

## Prerequisites

Participants should have:

- Basic understanding of cloud computing concepts and familiarity with Microsoft Azure services.
- Knowledge of data integration principles and experience with data formats and sources.
- Understanding of SQL and relational database concepts, and familiarity with data warehousing solutions.
- Familiarity with machine learning concepts and experience with programming languages like Python or R
- Understanding of distributed computing principles and experience with data processing frameworks like Apache Spark.

## Architecture


# Getting Started with Lab

1. Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the bottom of lab guide to switch to different exercises of the lab guide.

   ![07](./Images/gs/1a.png)

1. To get the lab environment details, you can select the **Environment Details** tab. Additionally, the credentials will also be emailed to your registered email address. You can also open the Lab Guide on separate and full window by selecting the **Split Window** from the lower right corner. Also, you can start, stop, and restart virtual machines from the **Resources** tab.

   ![08](./Images/gs/08.png)
 
    > You will see the DeploymentID value on **Environment Details** tab, use it wherever you see SUFFIX or DeploymentID in lab steps.


## Login to Azure Portal

1. In the JumpVM, click on Azure portal shortcut of Microsoft Edge browser which is created on desktop.

   ![09](./Images/gs/09.png)
   
1. On **Sign into Microsoft Azure** tab you will see login screen, in that enter following email/username and then click on **Next**. 
   * Email/Username: <inject key="AzureAdUserEmail"></inject>
   
     ![04](./Images/gs/04.png)
     
1. Now enter the following password and click on **Sign in**.
   * Password: <inject key="AzureAdUserPassword"></inject>
   
     ![05](./Images/gs/05.png)
     
   > If you see the pop-up click on **ask later**.

      ![06](./Images/gs/asklater1.png)
  
1. If you see the pop-up **Stay Signed in?**, click No

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Maybe Later** to skip the tour.
      












