# Lab 2: Secure data access in Microsoft Fabric

## Estimated Duration : 45 minutes

Microsoft Fabric has a multi-layer security model for managing data access. Security can be set for an entire workspace, for individual items, or through granular permissions in each Fabric engine. In this exercise, you secure data using workspace, and item access controls and OneLake data access roles

In this hands-on lab, you will learn how to secure data access within Microsoft Fabric by applying workspace access controls, item-level permissions, and OneLake data access roles. You'll experience how different levels of access impact the ability to view and interact with data in Data Warehouses and Lakehouses. By the end of this lab, you’ll understand how to configure and validate security settings at multiple layers to protect sensitive information in Microsoft Fabric.

## Lab Objectives

In this lab, you will complete the following tasks:

- Task 1: Create a data warehouse

- Task 2: Create a lakehouse

- Task 3: Apply workspace access controls

- Task 4: Apply item access control

- Task 5: Apply OneLake data access roles in a Lakehouse

### Task 1: Create a data warehouse

In this task, you will create a sample data warehouse named sample-dw prepopulated with taxi ride analysis data

1. On the menu bar on the left, select **Create**. In the *New* page, under the *Data Warehouse* section, select **Sample warehouse** and create a new data warehouse named **sample-dw**.

    >**Note**: If the **Create** option is not pinned to the sidebar, you need to select the ellipsis (**...**) option first.

    After a minute or so, a new warehouse will be created and populated with sample data for a taxi ride analysis scenario.

    ![Screenshot of a new warehouse.](./Images/sample-data-warehouse.png)

### Task 2: Create a lakehouse

In this task, you will create a new Lakehouse, populate it with sample data, and prepare it for access control exercises.

1. In the menu bar on the left, select **Workspaces** (the icon looks similar to 🗇).
1. Select the workspace you created.
1. In the workspace, select the **+ New Item** button and then select **Lakehouse**. Create a new Lakehouse with the name **lakehouse2**.
1. After a minute or so, a new Lakehouse will be created:

    ![Screenshot of a new lakehouse in Fabric.](./Images/lab5u13.png)

1. Select the **Start with sample data** tile, then on the **Use a Sample** page, choose the **Public holidays** tile to populate the workspace with sample data.

    ![Screenshot of a new lakehouse in Fabric.](./Images/lab5u14.png)

### Task 3: Apply workspace access controls

Workspace roles are used to control access to workspaces and the content within them. Workspace roles can be assigned when users need to see all items in a workspace, when they need to manage workspace access, or create new Fabric items, or when they need specific permissions to view, modify or share content in the workspace.  

In this task, you add a user to a workspace role, apply permissions and, see what is viewable when each set of permissions is applied. You open two browsers and sign-in as different users. In one browser, you'll be a **Workspace Admin** and in the other, you'll sign-in as a second, less privileged user. In one browser, the Workspace Admin changes permissions for the second user and in the second browser, you're able to see the effects of changing permissions.  

1. In the menu bar on the left, select **Workspaces** (the icon looks similar to &#128455;).
1. Next select the workspace you created.
1. Select on **Manage access** on the top of the screen.

    ![Screenshot of a new lakehouse in Fabric.](./Images/lab5u15.png)

    ![Screenshot of a new lakehouse in Fabric.](./Images/lab5u16.png)

    >**Note**: You'll see the user you're logged, who is a a member of the **Workspace Admin** role because you created the workspace. No other users are assigned access to the workspace yet.

1. Next, you'll see what a user without permissions on the workspace can view. In your browser, open an InPrivate window. In the Microsoft Edge browser, select the ellipse at the top right corner and select **New InPrivate Window**.

1. Enter *https://app.fabric.microsoft.com* and sign-in as the second user with the below credentials:

   - Email : <inject key="testuser" enableCopy="true"/>

   - Password : <inject key="test user Password" enableCopy="true"/>
  
1. On the bottom left corner of your screen, select **Microsoft Fabric** and then select **Data Warehouse**. Next select **Workspaces** (the icon looks similar to &#128455;).  

  > **Note:** The second user doesn't have access to the workspace, so it's not viewable.

1. Next, you assign the **Workspace Viewer** role to the second user and see that the role grants read access to the warehouse in the workspace.
  
1. Return to the browser window where you're logged in as the Workspace Admin. Ensure you're still on the page that shows the workspace you created. It should have your new workspace items, and the sample warehouse and lakehouse, listed at the bottom of the page.
1. Select **Manage access** at the top right of the screen.
1. Select **Add people or groups**. Enter the email of the second user you're testing with. Select **Add** to assign the user to the workspace **Viewer** role. 

    ![Screenshot of a new lakehouse in Fabric.](./Images/lab5u17.png)

1. Return to the InPrivate browser window where you're logged in as the second user and select refresh button on the browser to refresh session permissions assigned to the second user.

1. Select the **Workspaces** icon on the left menu bar (the icon looks similar to &#128455;) and select on the workspace name you created as the Workspace Admin user. The second user can now see all of the items in the workspace because they were assigned the **Workspace Viewer** role.

1. Select the warehouse and open it.

1. Select the **Date** table and wait for the rows to be loaded. You can see the rows because as a member of the Workspace Viewer role, you have CONNECT and ReadData permission on tables in the warehouse. For more information on permissions granted to the Workspace Viewer role, see [Workspace roles](https://learn.microsoft.com/en-us/fabric/data-warehouse/workspace-roles).

1. Next, select the **Workspaces** icon on the left menu bar, then select the *lakehouse2*.
1. When the lakehouse opens, click on the dropdown box at the top right corner of the screen that says **Lakehouse** and select **SQL analytics endpoint**.
1. Select the **publicholidays** table and wait for the data to be displayed. Data in the lakehouse table is readable from the SQL analytics endpoint because the user is a member of the Workspace Viewer role that grants read permissions on the SQL analytics endpoint.

### Task 4: Apply item access control

Item permissions control access to individual Fabric items within a workspace, like warehouses, lakehouses and semantic models. In this exercise, you remove the **Workspace Viewer** permissions applied in the previous exercise and then apply item level permissions on the warehouse so a less privileged user can only view the warehouse data, not the lakehouse data.

In this task, you will configure item-level permissions by granting access to specific Fabric items like warehouses, limiting user visibility to only assigned resources.

1. Return to the browser window where you're logged in as the Workspace Admin. Select **Workspaces** from the left navigation pane. 
2. Select the workspace that you created to open it.
3. Select **Manage access** from the top of the screen.
4. Select the word **Viewer** under the name of the second user. On the menu that appears, select **Remove**.

5. Close the **Manage access** section.
6. In the workspace, hover over the name of your warehouse and an ellipse (**...**) will appear. Select the ellipse and select **Manage permissions**

7. Select **Add user** and enter the name of the second user. 
8. In the box that appears, under **Additional permissions** check **Read all data using SQL (ReadData)** and uncheck all other boxes.

9. Select **Grant**

10. Return to the browser window where you're logged in as the second user. Refresh the browser view.  

11. The second user no longer has access to the workspace and instead has access to only the warehouse. You can no longer browse workspaces on the left navigation pane to find the warehouse. Select **OneLake** on the left navigation menu to find the warehouse. 

12. Select the warehouse. On the screen that appears, select **Open** from the top menu bar.

13. When the warehouse view appears, select the **Date** table to view table data. The rows are viewable because the user still has read access to the warehouse because ReadData permissions were applied by using item permissions on the warehouse.

### Task 5: Apply OneLake data access roles in a Lakehouse

OneLake data access roles let you create custom roles within a Lakehouse and grant read permissions to folders you specify. OneLake data access roles is currently a Preview feature.

In this task, you assign an item permission and create a OneLake data access role and experiment with how they work together to restrict access to data in a Lakehouse.  

1. Stay in the browser where you're logged in as the second user.  
2. Select **OneLake** on the left navigation bar. The second user doesn't see the lakehouse.  
3. Return to the browser where you're logged in as the Workspace Admin.
4. Select **Workspaces** on the left menu and select your workspace. Hover over the name of the lakehouse.  
5. Select on the ellipse (**...**) to the right of the ellipse and select **Manage permissions**
6. On the screen that appears, select **Add user**. 
7. Assign the second user to the lakehouse and ensure none of the checkboxes on the **Grant People Access** window are checked.  
8. Select **Grant**. The second user now has read permissions on the lakehouse. Read permission only allows the user to see metadata for the lakehouse but not the underlying data. Next we'll validate this.
9. Return to the browser where you're logged in as the second user. Refresh the browser.
10. Select **OneLake** in the left navigation pane.  
11. Select the lakehouse and open it. 
12. Select **Open** on the top menu bar. You're unable to expand the tables or files even though read permission was granted. Next, you grant the second user access to a specific folder using OneLake data access permissions.
13. Return to the browser where you're logged in as the workspace administrator.
14. Select **Workspaces** from the left navigation bar.
15. Select your workspace name.
16. Select the lakehouse.
17. When the lakehouse opens, select **Manage OneLake data access** on the top menu bar and enable the feature by clicking the **Continue** button.
18. Select new role on the **Manage OneLake data access (preview)** screen that appears.
19. Create a new role called **publicholidays** that can only access the publicholidays folder as shown in the screenshot below.
20. When the role finishes creating, select **Assign role** and assign the role to your second user, select **Add** and, select **Save**.
21. Return to the browser where you're logged in as the second user. Ensure you're still on the page where the lakehouse is open. Refresh the browser.  
22. Select the **publicholidays** table and wait for the data to load. Only the data in the publicholidays table is accessible to the user because the user was assigned to the custom OneLake data access role. The role permits them to see only the data in the publicholidays table, not data in any of the other tables, files, or folders.

## Review

In this lab, you learned how to:

- Create and manage a lakehouse in Microsoft Fabric.

- Ingest data into a lakehouse using a Dataflow Gen2.

- Query lakehouse data using a Spark notebook.

- Monitor and track activity execution history through the monitoring hub.

- Apply filters and customize columns to optimize the monitoring experience.

## Now, click on Next from the lower right corner to move on to the next lab.
