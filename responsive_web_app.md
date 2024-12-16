
---
Building a Responsive Web App
---

## Introduction

This tutorial teaches you how to create a Mendix Studio Pro responsive web app, which is compatible with all desktop, tablet, and mobile browsers. The resulting app is geared towards a hardware store wanting to manage its tool inventory.

You will learn key concepts such as working with [domain models](https://docs.mendix.com/refguide/domain-model/) and [entities](https://docs.mendix.com/refguide/entities/), adding [pages](https://docs.mendix.com/refguide/pages/) and populating them with data, and creating [microflows](https://docs.mendix.com/refguide/microflows/).


## Prerequisites

Before delving into this tutorial, make sure you have:

* A stable internet connection.
* A [free Mendix account](https://signup.mendix.com/link/signup/?source=quickstart-part1&medium=mxdocs&_gl=1*nrji6*_gcl_au*ODM2MTY3NDA0LjE3MzI1MzkyNzY.).
* Mendix Studio Pro [downloaded](https://marketplace.mendix.com/link/studiopro/) and [installed](https://docs.mendix.com/refguide/install/) on your machine.
If you use a Mac computer, complete the steps in [Configuring Parallels](https://docs.mendix.com/refguide/using-mendix-studio-pro-on-a-mac/) to install Studio Pro on your Mac.
* Read the [Studio Pro Overview](https://docs.mendix.com/refguide/studio-pro-overview/) for a walk-through of the Studio Pro interface.
	
## Creating your Responsive Web App

Follow these steps to create your app's structure, and all the objects needed to successfully run the app.

### Generating the App's Working Area

The [working area](https://docs.mendix.com/refguide/studio-pro-overview/#working-area) of an app is the canvas onto which you place the necessary objects.
1. Open Studio Pro and click **Create New App**. 
This opens the template selection window.
2. Select **Blank Web App**, then click **Use this starting point**.
This opens the **App Settings** window.
3. Name your app, then click **Create app**.
Allow a few minutes for the underlying steps to be performed.
Once they are completed, the app's working area opens, and the home page of the app, named **Home_Web**, is displayed.

### Populating the Domain Model

The [domain model](https://docs.mendix.com/refguide/domain-model/) holds the inter-related [entities](https://docs.mendix.com/refguide/entities/) that form an app's structure.
In the domain model, you need to create an entity to be used as the basis for the next steps.
1. Double-click your app's domain model in the **App Explorer**.
2. From the **Toolbox** pane, drag and drop an **Entity** object.
This will hold the tool database, along with its attributes.
3. Double-click the entity to open its properties window.
4. Add a suggestive name, such as **Tools**.
5. On the **Attributes** tab, click **New**.
This opens the **Add Attribute** window.
6. Add an attribute to hold the tool name. It should have the following characteristics:
    * **Name** = **Name**
    * **Type** = **String**
    * **Length** = **Unlimited**
7. Add another attribute to hold the tool code within the database. It should have the following characteristics:
    * **Name** = **Code**
    * **Type** = **AutoNumber**

### Generating Pages

These [pages](https://docs.mendix.com/refguide/pages/) serve as the interface of the app, allowing you to view and edit the tool database.
1. Right-click the entity you have just created and select **Generate overview pages**. 
This creates the **OverviewPages** menu item in the **App Explorer**, which includes two new pages suffixed with **_NewEdit** and **_Overview**, respectively. 
The **_NewEdit** page allows you to create or update an object.
The **_Overview** page lists objects of a single entity type.
2. Rename the new pages to something suggestive for your particular scenario, such as **Tools_New** and **Tools_Overview**.

### Configuring the App's Home Page

The home page is the first page you see upon opening the app, serving as the entry point to the tool database.
1. On the **Home_Web** page, access the **Building Blocks** section of the **Toolbox** pane.
2. Find the **Card Action** building block and drag it to the **Home_Web** canvas.
3. Click the **Card title** element of the card action.
In the **Properties** pane that opens for the card title, set the **Caption** to **Tools**.
4. Click the **Button** element of the card action.
In the **Properties** pane that opens for the button, set the **On click** action to **Show a page**. 
This displays the **Select web page** window, where you need to select the **Tools_Overview** page you have created at step 8 in the previous sequence.
This means that, once you click the button on the home page, you are taken to the tool list page.
5. Access the **Navigation** menu of your app in the **App Explorer**.
6. In the **Home pages** section, click **Select** next to the **Default home page** field, and choose the **Home_Web** item.

### Creating the Tool Addition and Editing Logic

The logic behind adding, editing, and confirming changes is dictated by a [microflow](https://docs.mendix.com/refguide/microflows/).
1. Access the **Tools_New** page, and click the **Save** button to open its properties.
2. In the **Properties** pane, set the **On click** event to **Call a microflow**.
This opens the **Select Microflow** window.
3. Select the folder where you want the microflow to reside, then click **New**.
4. Give the microflow a suggestive name, then click **OK**.
You might notice that the new microflow is associated to the **Tools** entity you created earlier.
5. Open the microflow and start adding actions to it:
5.1. Add a **Create object** action, and set its **Entity** to the **Tools** entity you created earlier.
Add a suggestive name, such as **NewTools**, then click **OK**.
This allows you to add new objects to the database.
5.2. Add a **Change object** action, and set its **Object** to the **NewTools** item you created at the previous step, then click **OK**.
This allows you to edit the **NewTools** item you have just created. In the current scenario, this means adding a new tool.
5.3. Add a **Commit change** action, and set its **Object or List** to the **NewTools** item you created at the previous step, then click **OK**.
This allows you to store the change you have just made to the database. In the current scenario, this means storing the newly added tool to the tool database.
5.4. Add a **Show information message** action, and set it to display the **Tool saved successfully message**, then click **OK**.
5.5. Add a **Close page** action to automatically close the tool addition window.

### Testing and Deploying the App

Once you have completed all the previous steps, and saved all your changes, you can test the app.
1. Click **Run locally**.
This step builds your app, so it might take a few moments.
2. Click **View App**.
This opens your app in a browser, ready for testing.

