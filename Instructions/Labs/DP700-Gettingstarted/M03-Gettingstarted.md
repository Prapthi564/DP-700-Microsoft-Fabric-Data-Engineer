# DP-700: Microsoft-Fabric-Data-Engineer Workshop

Welcome to your DP-700: Microsoft-Fabric-Data-Engineer Workshop! We've prepared a seamless environment for you to explore and learn Azure Services. Let's begin by making the most of this experience.

### Overall Estimated timing: 75 minutes

In this hands-on lab, you will build an end-to-end real-time data streaming solution. You will start by creating an eventhouse and an eventstream to manage and process incoming data. You will then add a data source and configure a destination to route the processed data appropriately. After setting up the streaming infrastructure, you will create a real-time dashboard to visualize the data, including building a base query, adding parameters for dynamic insights, and customizing the dashboard with additional pages. Finally, you will configure auto-refresh settings to keep the data current and learn how to save and share the dashboard for collaboration.

## Objectives

By the end of this lab series, you will be able to create and manage a Microsoft Fabric eventhouse, configure eventstreams with real-time data sources and destinations, and build interactive real-time dashboards using base queries, parameters, and auto-refresh features to visualize and share live data insights effectively.

1. **Create an eventhouse**: You will learn how to create an eventhouse in Microsoft Fabric, which provides a centralized and scalable foundation for capturing and storing streaming data. This task will guide you through creating a workspace, setting up the eventhouse, and understanding how real-time event data is organized and persisted for downstream analytics.

1. **Create an eventstream**: You will learn how to add a data source to your eventstream in Microsoft Fabric to enable real-time data ingestion. This task will guide you through connecting an external system—such as an Event Hub, IoT Hub, or other streaming service—as a source, allowing your eventstream to begin capturing and processing live event data.

1. **Add a source**: You will learn how to add a destination to your eventstream in Microsoft Fabric, enabling it to route processed data to storage or analytics platforms such as a lakehouse or KQL database for real-time insights and further processing.

1. **Add a destination**: You will learn how to add a destination to your eventstream in Microsoft Fabric, enabling processed streaming data to be routed to storage or analytics tools such as a lakehouse or KQL database for further use.

1. **Create a real-time dashboard**: You will learn how to create a real-time dashboard in Microsoft Fabric to visualize and monitor live data from your eventstream, enabling instant insights and responsive decision-making.

1. **Create a base query**: You will learn how to create a base query in Microsoft Fabric to streamline your dashboard visuals by centralizing common data logic, improving efficiency and maintainability.

1. **Add a parameter**: You will learn how to add a parameter to your Microsoft Fabric dashboard, allowing you to filter and display data based on specific criteria, such as selecting a neighborhood to focus on for more targeted insights.

1. **Add a page**: You will learn how to add multiple pages to your Microsoft Fabric dashboard, enabling you to organize and display different sets of data across different views for a more comprehensive and interactive experience.

1. **Configure auto refresh**: You will learn how to configure auto-refresh for your Microsoft Fabric dashboard, enabling automatic data updates at specified intervals to keep your visualizations up-to-date with the latest information without requiring manual intervention.

1. **Save and share the dashboard**: You will learn how to save and share your Microsoft Fabric dashboard, enabling you to store your work and grant access to other users for collaborative analysis and decision-making based on real-time data insights.


## Pre-requisites

- Basic knowledge of Microsoft Fabric, including creating and managing workspaces and resources.
- Understanding of how to create and configure dashboards for data visualization.
- Familiarity with querying and data manipulation using base queries for real-time data processing.
- Basic knowledge of configuring automatic updates and refreshing visualizations in dashboards.


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

## Lab Duration Extension

1. To extend the duration of the lab, kindly click the **Hourglass** icon in the top right corner of the lab environment. 

    ![Manage Your Virtual Machine](../Images/dpg5.png)

    >**Note:** You will get the **Hourglass** icon when 10 minutes are remaining in the lab.

2. Click **OK** to extend your lab duration.
 
   ![Manage Your Virtual Machine](../Images/dpg6.png)

3. If you have not extended the duration prior to when the lab is about to end, a pop-up will appear, giving you the option to extend. Click **OK** to proceed.

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:
 
   ![Launch Azure Portal](../Images/dpg7.png)

1. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../Images/dpg8.png)
 
1. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
     ![Enter Your Password](../Images/dpg9.png)
 
1. If prompted to stay signed in, you can click **No**.

1. If **Action required** pop-up window appears, click on **Ask later**.
   
    ![](../Images/dpg10.png)
 
1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **Cancel**.

## Steps to Proceed with MFA Setup if the "Ask Later" Option is Not Visible

1. If you see the pop-up **Stay Signed in?**, click **No**.

1. If **Action required** pop-up window appears, click on **Next**.
   
   ![](../Images/dpg11.png)

1. On **Start by getting the app** page, click on **Next**.
1. Click on **Next** twice.
1. In **android**, go to the play store and Search for **Microsoft Authenticator** and Tap on **Install**.

   ![Install](../Images/dpg12.png)

   > Note: For Ios, Open the app store and repeat the steps.

   > Note: Skip if already installed.

1. Open the app and tap on **Scan a QR code**.

1. Scan the QR code visible on the screen **(1)** and click on **Next (2)**.

   ![QR code](../Images/dpg13.png)

1. Enter the digit displayed on the Screen in the Authenticator app on mobile and tap on **Yes**.

1. Once the notification is approved, click on **Next**.

   ![Approved](../Images/dpg14.png)

1. Click on **Done**.

1. If prompted to stay signed in, you can click **"No"**.

1. Tap on **Finish** in the Mobile Device.

   > NOTE: While logging in again, enter the digits displayed on the screen in the **Authenticator app** and click on Yes.

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **"Cancel"** to skip the tour.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.


## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels explicitly tailored for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.
 
Learner Support Contacts:
 
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Click on **Next** from the lower right corner to move on to the next page.

   ![Start Your Azure Journey](../Images/dpn1.png)

## Happy Learning !!
