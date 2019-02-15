---
title: "Data Sources | MicrosoftDocs"
description: Text to go here
ms.custom: ""
ms.date: 11/05/2018
ms.reviewer: ""
ms.service: "dynamics-365-ai"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "Dynamics 365 (online)"
  - "Dynamics 365 Version 9.x"
ms.assetid: 
caps.latest.revision: 31
author: "jimholtz"
ms.author: "jimholtz"
manager: "kvivek"
robots: noindex,nofollow
---
# Data Sources

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

**You can bring in data to Customer Insights by using the 20+ out-of-the-box connectors** that we make available for sources such as Dynamics 365, SQL Azure, and Blob store. Even if you don’t find a suitable out-of-the-box connector for your source, **you can always export the data from your source as a CSV. file and import to Customer Insights using our CSV connector.** To import data to Customer Insights, you need to create a data source in the Data Sources screen. It’s recommended to have multiple data sources as it will allow you to have different refresh schedules and credentials for each of your data sources.

## Bring your data into Customer Insights 

***Important Note***: At this point, on-prem data sources are not supported in Customer Insights. 
We hope to enable that option in the future.

### Step 1 (mandatory): Creating a new data source on the Data Sources screen
To load data to Customer Insights follow the following process:

1. Navigate to **Data Sources** from the **Data Manager page:**

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-tile.png "Get data tile")

2. Click **Get data** as shown below:

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-add.png "Get data add")

3. **Provide a name** for the data source and select **Save**. This will create the data source for you. 

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-create.png "Get data create")

4. Pick one of the many available connectors that are available in the screen below.
- **Note that some of the following data sources are not supported at this point, including OData**. 

  > [!div class="mx-imgBorder"] 
  > ![](media/data-manager-get-select-source.png "Get data select source")

- **If you wish to load data from Dynamics 365, make sure to choose the  *Common Data Service for Apps* connector shown below:

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-connection-settings.png "Get data connection settings")
   
- **Lastly, note that some of the following connectors replaced older connector versions. For example, if you wish to utilize the Dynamics 365 AX connector, you should choose the *Common Data Service for Apps* option.**

5. After choosing a connector, you will be required to fill some fields. For further guidance around filling those fields for some of the most common data sources (Dynamics 365, csv. and Text files, Blub storage, Azure SQL Database, etc), review the **Common Connectors Guidance** sub-section **that can be found under this section** in the left table of contents.  

### Step 2 (mandatory): Adding and Reviewing Entities
Within the next step you will add **entities** to your data source. In Customer Insights **entities are datasets**. For example, If you have a database that includes multiple datasets, each of these datasets is an **entity** (an **Orders** dataset, a **Sales** dataset, etc). 

1. Use the power query window shown below to review and possibly configure the data. The entities that the system identified in your selected datasource will appear on the left (shown in red).

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-configure-edit-queries.png "Edit queries")
   
You can add additional entities to your data source by clicking **Get Data**:

// 1

2. In this step you can also **edit and transform the data**: First choose an entity to edit or transform and then use one of the menus located at top of the Power Query window to find a specific transformation (those are shown in blue above). Also note that upon the selection of each transformation, it will be added as a processing *Step*. You can view and remove *Steps* in the part shown in green above. Exploring how your data looks like after a specific subset of added steps can be done by clicking on the final step in that subset.

While being optional, to avoid data-related issues, **you should complete the next few transformations:**

- If you are ingesting data from a .CSV file and the first row has headers you should open the **Transform Table** menu and then click the **Use headers as first row** option:

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-transform-table.png "Get data transform table")

- In addition, it is recommended to map your data to standard format of data. Customer Insights allows you to map your data to the **Microsoft Common Data Model (CDM)**. In order to do so, select **Map to Standard**, and then map fields from your source data to CDM fields:

  > [!div class="mx-imgBorder"] 
  > ![](media/data-manager-get-data-map-entity.png "Map to standard entity")

3. Click **Create** at the bottom of the power query screen to save:

   > [!div class="mx-imgBorder"] 
   > ![](media/configure-data-edit-queries-create.png "Create")

4. After saving, you can expect to see your datasource added in the **Data Sources** screen:

   > [!div class="mx-imgBorder"] 
   > ![](media/configure-data-datasource-added.png "Datasource added")

For each of your ingested datasources, beyond it's name, you can expect to see the last time the data was refreshed for that datasource, as well as it's status. There are three possible status: 
1. Data was successfully ingested (example is shown in blue in the image above)
2. No data was ingested yet (example is shown in red in the image above)
3. Data is still loading into Customer Insights (represented by a *warning sign* icon)

At this point you should refresh the datasource that you have just saved. Click the button highlighted below in red and then hit **Refresh** as highlighted in blue:

> [!div class="mx-imgBorder"] 
> ![](media/configure-data-sources-refresh.png "Data sources refresh")

Note: In the future this step will happen automatically.

**At this point, repeat the same steps for each datasource you wish to ingest into Customer Insights.**

### Step 3 (optional): Reviewing Ingested Data
It is possible that the data load will take some time. After successfully refreshing, the ingested data can be reviewed from the **Entities page** as shown below. For more information on the **Entity Page** visit the **Entities section**.

> [!div class="mx-imgBorder"] 
> ![](media/data-manager-entities-data.png "Data manager entities")

### Step 4 (optional) Editing existing data sources
**Note: The Edit operation is only available for Data sources that are not currently refreshing.** 

Follow the below steps to edit an existing data source: 

1. Browse to the data source that you wish to edit:

   > [!div class="mx-imgBorder"] 
   > ![](media/data-manager-get-data-source.png "Get data source")

2. Click on the **Edit** button to edit the data source in Power Query: 

   > [!div class="mx-imgBorder"] 
   > ![](media/configure-data-sources-edit2.png "Edit data source")

3. Don't forget to hit **Create** in the Power Query screen upon completing the edits in order to save your changes. If you wish to remove a data source, click **Delete** for that data source:

   > [!div class="mx-imgBorder"] 
   > ![](media/configure-data-sources-delete.png "Data sources delete")

### Next steps:
At this point you are ready to unlock unique customer insights through the mandatory **Configure Data** sections (those include **Map**,**Match** and **Merge**). If you first wish to review all the entities that were ingested, visit the **Entities** section first. 
