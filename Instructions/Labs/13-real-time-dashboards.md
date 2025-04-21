# Lab 1: Get started with Real-Time Dashboards in Microsoft Fabric

## Estimated Duration: 75 minutes

Real-time dashboards in Microsoft Fabric enable you to visualize and explore streaming data using the Kusto Query Language (KQL).   
                         
In this hands-on lab, you will build an end-to-end real-time data streaming solution. You will start by creating an eventhouse and an eventstream to manage and process incoming data. You will then add a data source and configure a destination to route the processed data appropriately. After setting up the streaming infrastructure, you will create a real-time dashboard to visualize the data, including building a base query, adding parameters for dynamic insights, and customizing the dashboard with additional pages. Finally, you will configure auto-refresh settings to keep the data current and learn how to save and share the dashboard for collaboration.

## Lab Objectives

In this lab, you will complete the following tasks:

- Task 1: Create an eventhouse
- Task 2: Create an eventstream
- Task 3: Add a source
- Task 4: Add a destination
- Task 5: Create a real-time dashboard
- Task 6: Create a base query
- Task 7: Add a parameter
- Task 8: Add a page
- Task 9: Configure auto refresh
- Task 10: Save and share the dashboard

## Task 1: Create an eventhouse

In this task, you will create an eventhouse, which serves as the foundation for organizing and storing your streaming data.

1. In the workspace, select **+ New item (1)**. In the *New item* pane, select **Eventhouse (2)**.

   ![Screenshot of alert settings.](./Images/md83.png)

1. Enter **BicycleEventhouse (1)** in the name field and select **Create (2)**

    ![Screenshot of alert settings.](./Images/md84.png)

1. Close any tips or prompts that are displayed until you see your new empty eventhouse.

1. In the pane on the left, note that your eventhouse contains a KQL database with the same name as the eventhouse.

1. Select the KQL database to view it.

    ![Screenshot of alert settings.](./Images/md85.png)

    >**Note**: Currently there are no tables in the database. In the rest of this exercise you'll use an eventstream to load data from a real-time source into a table.

## Task 2: Create an eventstream

In this task, you will set up an eventstream within the eventhouse to define how incoming events are processed and managed.

1. In the main page of your **KQL database (1)**, select **Get data (2)**.

2. For the data source, select **Eventstream (3)** > **New eventstream (4)**. Name the Eventstream `Bicycle-data` (5) and click on **Create (6)**.

   >**Note**: The creation of your new event stream in the workspace will be completed in just a few moments. Once established, you will be automatically redirected to the primary editor, ready to begin integrating sources into your event stream.

    ![Screenshot of alert settings.](./Images/md86.png)

    ![Screenshot of alert settings.](./Images/md87.png)

    ![Screenshot of a new eventstream.](./Images/md88.png)

### Task 3: Add a source

In this task, you will configure a data source for your eventstream to ingest real-time data from an external system.

1. In the Eventstream canvas, select **Use sample data**.

2. Name the source `Bicycles` (1), and select the **Bicycles (2)** sample data and select **Add (3)**

    ![Screenshot of a new eventstream.](./Images/md89.png)

   >**Note**: Your stream will be mapped and you will be automatically displayed on the **eventstream canvas**.

   ![Review the eventstream canvas](./Images/md90.png)

### Task 4: Add a destination

In this task, you will set up a destination that will receive the processed data from the eventstream for storage, analysis, or further processing.

1. Select the **Transform events or add destination (1)** tile and search for **Eventhouse (2)**.

   ![Review the eventstream canvas](./Images/md91.png)

1. In the **Eventhouse** pane, configure the following setup options.

   - **Data ingestion mode:**: Event processing before ingestion (1)
   - **Destination name:** `bikes-table` (2)
   - **Workspace:** fabric-<inject key="DeploymentID" enableCopy="false"/> (3)
   - **Eventhouse**: BicycleEventhouse (4)
   - **KQL database:** BicycleEventhouse (5)
   - **Destination table:** Create a new table named `bikes` 
   - **Input data format:** JSON (9)

   ![Eventstream destination settings.](./Images/md93.png)

   ![Eventstream destination settings.](./Images/md94.png)

   ![Eventstream destination settings.](./Images/md92.png)

1. In the **Eventhouse** pane, select **Save (10)**

1. On the toolbar, select **Publish**.

   ![Eventstream destination settings.](./Images/md95.png)

1. Wait a minute or so for the data destination to become active. Then select the **bikes-table** node in the design canvas and view the **Data preview** pane underneath to see the latest data that has been ingested:

   ![Eventstream destination settings.](./Images/md96.png)

1. Wait a few minutes and then use the **Refresh** button to refresh the **Data preview** pane. The stream is running perpetually, so new data may have been added to the table.

### Task 5: Create a real-time dashboard

In this task, you will create a real-time dashboard to visualize and monitor the data flowing through your eventstream.

1. In the menu bar on the left, select **+ create** to create a new **Real-Time Dashboard** named `bikes-dashboard`.

    ![A screenshot of a new dashboard.](./Images/md2-39.png)

    ![A screenshot of a new dashboard.](./Images/md2-40.png)

   >**Note**: A new empty dashboard is created.

1. In the toolbar, select **New data source (1)** and select **Eventhouse/KQL Database (2)** data source. Then select **BicycleEventhouse (3)** and click on **Connect (4)**

    ![A screenshot of a new dashboard.](./Images/md2-41.png)

    ![A screenshot of a new dashboard.](./Images/md2-42.png)

 1. Create a new data source with the following settings and click on **Add (4)**

    - **Display name**: `Bike Rental Data` (1)
    - **Database**: *BicycleEventhose (2)*.
    - **Passthrough identity**: *Selected*

    ![A screenshot of a new dashboard.](./Images/md2-43.png)

1. Close the **Data sources** pane, and then on the dashboard design canvas, select **Add tile**.

1. In the query editor, ensure that the **Bike Rental Data (2)** source is selected and enter the following KQL code:

    ```kql
    bikes
        | where ingestion_time() between (ago(30min) .. now())
        | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
        | project Neighbourhood, latest_observation, No_Bikes, No_Empty_Docks
        | order by Neighbourhood asc
    ```

1. **Run (3)** the query, which shows the number of bikes and empty bike docks observed in each neighbourhood in the last 30 minutes.

1. **Apply changes (5)** to see the data shown in a table in the tile on the dashboard.

   ![A screenshot of a dashboard with a tile containing a table.](./Images/md2-44.png)

   ![A screenshot of a dashboard with a tile containing a table.](./Images/md2-45.png)

1. On the tile, select the **Edit** icon (which looks like a pencil). Then in the **Visual Formatting** pane, set the following properties:
    - **Tile name**: Bikes and Docks
    - **Visual type**: Bar chart
    - **Visual format**: Stacked bar chart
    - **Y columns**: No_Bikes, No-Empty_Docks
    - **X column**: Neighbourhood
    - **Series columns**: infer
    - **Legend location**: Bottom

    ![A screenshot of a dashboard with a tile containing a table.](./Images/md2-46.png)

    ![A screenshot of a dashboard with a tile containing a table.](./Images/md2-47.png)

1. Apply the changes and then resize the tile to take up the full height of the left side of the dashboard.

    ![A screenshot of a dashboard with a tile containing a table.](./Images/md2-48.png)

1. In the toolbar, select **New tile**

1. In the query editor, ensure that the **Bike Rental Data** source is selected and enter the following KQL code:

    ```kql
    bikes
        | where ingestion_time() between (ago(30min) .. now())
        | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
        | project Neighbourhood, latest_observation, Latitude, Longitude, No_Bikes
        | order by Neighbourhood asc
    ```

1. Run the query, which shows the location and number of bikes observed in each neighbourhood in the last 30 minutes.

1. Apply the changes to see the data shown in a table in the tile on the dashboard.

1. On the tile, select the **Edit** icon (which looks like a pencil). Then in the **Visual Formatting** pane, set the following properties:
    - **Tile name**: Bike Locations
    - **Visual type**: Map
    - **Define location by**: Latitude and longitude
    - **Latitude column**: Latitude
    - **Longitude column**: Longitude
    - **Label column**: Neighbourhood
    - **Size**: Show
    - **Size column**: No_Bikes

1. Apply the changes, and then resize the map tile to fill the right side of the available space on the dashboard:

   ![A screenshot of a dashboard with a chart and a map.](./Images/md2-49.png)

### Task 6: Create a base query

Your dashboard contains two visuals that are based on similar queries. To avoid duplication and make your dashboard more maintainable, you can consolidate the common data into a single *base query*.

In this task, you will design a base query to retrieve and structure the data that will populate the visualizations on your dashboard.

1. On the dashboard toolbar, select **Base queries**. Then select **+Add**.

1. In the base query editor, set the **Variable name** to `base_bike_data` (1) and ensure that the **Bike Rental Data (2)** source is selected. Then enter the following query (3):

    ```kql
    bikes
        | where ingestion_time() between (ago(30min) .. now())
        | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
    ```
1. **Run (4)** the query and verify that it returns all of the columns needed for both visuals in the dashboard (and some others).

   ![A screenshot of a base query.](./Images/md2-50.png)

1. Select **Done** and then close the **Base queries** pane.

1. Edit the **Bikes and Docks** bar chart visual, and change the query to the following code:

    ```kql
    base_bike_data
    | project Neighbourhood, latest_observation, No_Bikes, No_Empty_Docks
    | order by Neighbourhood asc
    ```

1. Apply the changes and verify that the bar chart still displays data for all neighborhoods.

1. Edit the **Bike Locations** map visual, and change the query to the following code:

    ```kql
    base_bike_data
    | project Neighbourhood, latest_observation, No_Bikes, Latitude, Longitude
    | order by Neighbourhood asc
    ```

1. Apply the changes and verify that the map still displays data for all neighborhoods.

### Task 7: Add a parameter

Your dashboard currently shows the latest bike, dock, and location data for all neighborhoods. Now lets add a parameter so you can select a specific neighborhood.

In this task, you will add a parameter to your base query to enable dynamic filtering and interactivity within the dashboard.

1. On the dashboard toolbar, on the **Manage** tab, select **Parameters**.
1. Note any existing parameters that have been automatically created (for example a *Time range* parameter). Then **Delete** them.
1. Select **+ Add**.
1. Add a parameter with the following settings:
    - **Label**: `Neighbourhood`
    - **Parameter type**: Multiple selection
    - **Description**: `Choose neighbourhoods`
    - **Variable name**: `selected_neighbourhoods`
    - **Data type**: string
    - **Show on pages**: Select all
    - **Source**: Query
    - **Data source**: Bike Rental Data
    - **Edit query**:

        ```kql
        bikes
        | distinct Neighbourhood
        | order by Neighbourhood asc
        ```

    - **Value column**: Neighbourhood
    - **Label column**: Match value selection
    - **Add "Select all" value**: *Selected*
    - **"Select all" sends empty string**: *Selected*
    - **Auto-reset to default value**: Selected
    - **Default value**: Select all

1. Select **Done** to create the parameter.

    Now that you've added a parameter, you need to modify the base query to filter the data based on the chosen neighborhoods.

1. In the toolbar, select **Base queries**. Then select the **base_bike_data** query and edit it to add an **and** condition to the **where** clause to filter based on the selected parameter values, as shown in the following code:

    ```kql
    bikes
        | where ingestion_time() between (ago(30min) .. now())
          and (isempty(['selected_neighbourhoods']) or Neighbourhood  in (['selected_neighbourhoods']))
        | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
    ```

1. Select **Done** to save the base query.

1. In the dashboard, use the **Neighbourhood** parameter to filter the data based on the neighborhoods you select.

   ![A screenshot of a dashboard with parameters selected.](./Images/md2-51.png)

1. Select **Reset** to remove the selected parameter filters.

### Task 8: Add a page

Your dashboard currently consists of a single page. You can add more pages to provide more data.

In this task, you will add an additional page to your dashboard to organize different visualizations and enhance usability.

1. On the left side of the dashboard, expand the **Pages** pane; and select **+ Add page**.
1. Name the new page **Page 2**. Then select it.
1. On the new page, select **+ Add tile**
1. In the query editor for the new tile, enter the following query:

    ```kql
    base_bike_data
    | project Neighbourhood, latest_observation
    | order by latest_observation desc
    ```

1. Apply the changes. Then resize the tile to fill the height of the dashboard.

   ![img](./Images/md2-52.png)

### Task 9: Configure auto refresh

Users can manually refresh the dashboard, but it may be useful to have it automatically refresh the data at a set interval.

In this task, you will configure the dashboard’s auto-refresh settings to ensure that the data visualizations are updated in real time.

1. On the dashboard toolbar, on the **Manage** tabe, select **Auto refresh**.

1. In the **Auto refresh** pane, configure the following settings:

    - **Enabled**: *Selected*
    - **Minimum time interval**: Allow all refresh intervals
    - **Default refresh rate**: 30 minutes

1. Apply the auto refresh settings.

### Task 10: Save and share the dashboard

Now you have a useful dashboard, you can save it and share it with other users.

In this task, you will save your dashboard and configure sharing settings to collaborate with others and allow broader access to real-time insights.

1. On the dashboard toolbar, select **Save**.

1. When the dashboard is saved, select **Share**.

1. On the **Share** dialog box, select **Copy link** and copy the link to the dashboard to the clipboard.

1. Open a new browser tab and paste the copied link to navigate to the shared dashboard. Sign in again with your credentials if prompted.

1. Explore the dashboard, using it to see the latest information about bikes and empty bike docks across the city.

### Review    

In this lab, you learned how to:

- Create and configure an eventhouse for managing real-time event data.
- Set up an eventstream to process and organize incoming events.
- Add a source to ingest real-time data into the eventstream.
- Add a destination to route processed data for storage or further analysis.
- Create a real-time dashboard to visualize streaming data.
- Build a base query to retrieve and structure dashboard data.
- Add parameters to make dashboard queries dynamic and interactive.
- Add additional pages to the dashboard for better organization.
- Configure auto-refresh to keep dashboard visualizations updated in real time.
- Save and share the dashboard to collaborate and provide real-time insights to others.

