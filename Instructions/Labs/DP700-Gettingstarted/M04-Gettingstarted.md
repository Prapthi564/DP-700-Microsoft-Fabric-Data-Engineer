# DP-700: Microsoft-Fabric-Data-Engineer Workshop

Welcome to your DP-700: Microsoft-Fabric-Data-Engineer Workshop! We've prepared a seamless environment for you to explore and learn Azure Services. Let's begin by making the most of this experience.

### Overall Estimated timing: 4 hrs

In this hands-on lab, you'll explore core and advanced concepts of data warehousing using Microsoft Fabric. You'll begin by creating and loading data into a Fabric data warehouse using T-SQL, and then query and analyze the data using built-in SQL tools. You'll also monitor performance using dynamic management views and query insights. Finally, you'll implement security measures like dynamic data masking, row-level, and column-level security to protect sensitive information and manage access effectively. By the end, you'll have practical experience building, managing, and securing a modern data warehouse in Microsoft Fabric.


## Objectives

By the end of this lab series, you will be able to create, manage, and secure a Microsoft Fabric data warehouse, load and query data using T-SQL, monitor performance, and implement advanced security for enterprise-scale analytics.

1. **Analyze data in a data warehouse**: You will learn how to create a data warehouse in Microsoft Fabric that supports large-scale analytics with full SQL capabilities. This lab will guide you through defining tables, building a relational model, running queries, and visualizing results through integrated reports.

1. **Load data into a warehouse using T-SQL**: You will learn how to load data into a Microsoft Fabric data warehouse using T-SQL for scalable analytics. This lab walks you through creating a lakehouse, defining tables, and using stored procedures to populate and validate a structured data warehouse.

1. **Query a data warehouse in Microsoft Fabric**: You will learn how to query a data warehouse in Microsoft Fabric using T-SQL to explore and validate data. This lab guides you through creating a warehouse, running analytical queries, and building filtered views for reporting in a high-performance environment.

1. **Monitor a data warehouse in Microsoft Fabric**: You will learn how to monitor a data warehouse in Microsoft Fabric using dynamic management views (DMVs) and query insights. This lab will guide you through tracking current activity and analyzing historical performance to ensure efficient query execution and system health.

1. **Secure a Microsoft Fabric data warehouse**: You will learn how to secure a Microsoft Fabric data warehouse by implementing dynamic data masking, row-level and column-level security, and granular SQL permissions. This lab will help you protect sensitive data and manage user access effectively within your data environment.


## Pre-requisites

- Basic understanding of data warehousing concepts and relational database design
- Familiarity with writing and executing T-SQL queries
- General knowledge of data loading, transformation, and reporting workflows

## Architecture

In this hands-on lab, the architecture flow includes several essential components.

1. **Create a Microsoft Fabric Lakehouse**: Learning how to create a lakehouse in Microsoft Fabric to unify the capabilities of a data lake and data warehouse. This includes setting up a centralized storage location for structured and unstructured data and preparing it for large-scale analytics and processing tasks.

1. **Use Delta Tables in Apache Spark**:
Exploring how to use Delta Tables within Microsoft Fabric to manage large datasets with ACID compliance and schema enforcement. This task involves creating Delta tables using Spark, querying them with SQL, and understanding how they support both batch and streaming data operations efficiently.

1. **Create a medallion architecture in a Microsoft Fabric lakehouse**:
Implementing the medallion architecture model (bronze, silver, and gold layers) to organize data workflows in a Fabric lakehouse. This includes using Spark notebooks to transform raw data through each layer, enhancing data quality, optimizing performance, and making it ready for analytics and reporting.


## Architecture Diagram

 ![](../Images/dp900m2arc.png)

## Explanation of Components

1. **Fabric Lakehouse**: A Fabric Lakehouse is a data architecture in Microsoft Fabric that combines the features of a data lake and a data warehouse into a unified platform. It enables organizations to store, manage, and analyze structured, semi-structured, and unstructured data at scale using familiar tools and languages like SQL, Apache Spark, and Python.

1. **Apache Spark**: It is an open-source, distributed computing engine designed for fast and large-scale data processing. It’s widely used in big data environments for tasks such as data transformation, machine learning, and real-time analytics. 

1. **Medallion architecture**: It is a design pattern that organizes data into three layers (Bronze, Silver, and Gold) to improve data quality and structure as it progresses through each stage, facilitating optimized analytics. 


# Getting Started with lab
 
Welcome to your DP-700: Microsoft Fabric Data Engineer Workshop! We've prepared a seamless environment for you to explore and learn about data engineering concepts and related Microsoft Fabric services. Let's begin by making the most of this experience:
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **lab guide** will be right at your fingertips within your web browser.
 
![Access Your VM and Lab Guide](../Images/dpg17.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
![Explore Lab Resources](../Images/dpg1.png)

## Lab Guide Zoom In/Zoom Out
 
To adjust the zoom level for the environment page, click the **A↕: 100%** icon located next to the timer in the lab environment.

![](../Images/dpg2.png)

## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![Use the Split Window Feature](../Images/dpg3.png)

## Managing Your Virtual Machine
 
Feel free to **start, stop, or restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../Images/dpg4.png)


## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels explicitly tailored for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.
 
Learner Support Contacts:
 
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Click on **Next** from the lower right corner to move on to the next page.

   ![Start Your Azure Journey](../Images/dpn2.png)

## Happy Learning !!
