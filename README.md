# Restful interactions with z/OS from containers

In this workshop, you will work with Node-RED. You will have the option to run Node-RED in IBM Cloud as a service or through Docker on IBM Cloud. We have created a website through the Node-RED dashboard nodes to interact with z/OS.

Once you've imported your flow into Node-RED you'll be working with a website like the one shown below. ![Node-RED Website](img/website.png)

We are providing you with step-by-step directions to create this website for your. Just follow the actions below.

## Create a Node-RED service on IBM Cloud
There are two ways that you can create a Node-RED service on IBM Cloud. Running Node-RED in Docker on IBM Cloud starts up a bit faster initially. Other then that, they're exactly the same. You can choose whichever way you'd like and both are documented below. The Node-RED in Docker will be shown during the session.

### Option 1: Node-RED in Docker on IBM Cloud
Before we can use Docker to push a Node-RED container to IBM Cloud, we need to setup the pre-requisites.

**Pre-requisites**

* Create an IBM Cloud account: [https://www.ibm.com/uk-en/cloud/free](https://www.ibm.com/uk-en/cloud/free)
* Run Docker on your local workstation: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
* Create a Docker Hub account: [https://hub.docker.com/signup](https://hub.docker.com/signup)
* Setup IBM Cloud CLI on your local worksation: [https://cloud.ibm.com/docs/cli](https://cloud.ibm.com/docs/cli)

**Run Node-RED container in IBM Cloud**

1. `ibmcloud cf push Code-Think-NodeRED --docker-image nodered/node-red:1.1.3-10-amd64 --docker-username <docker-user>  -m 256M  --random-route`

```
~ ibmcloud cf push Code-Think-NodeRED --docker-image nodered/node-red:1.1.3-10-amd64 --docker-username jennfrancis  -m 256M  --random-route
Invoking 'cf push Code-Think-NodeRED --docker-image nodered/node-red:1.1.3-10-amd64 --docker-username jennfrancis -m 256M --random-route'...

Environment variable CF_DOCKER_PASSWORD not set.
Docker password:
Pushing app Code-Think-NodeRED to org jenn.francis@ibm.com / space dev as Jenn.Francis@ibm.com...
Getting app info...
Creating app with these attributes...
+ name:              Code-Think-NodeRED
+ docker image:      nodered/node-red:1.1.3-10-amd64
+ docker username:   jennfrancis
+ memory:            256M
  routes:
+   code-think-nodered-friendly-nyala.eu-gb.mybluemix.net

Creating app Code-Think-NodeRED...
Mapping routes...

Staging app and tracing logs...
   Cell 5f4df484-e14b-4e86-8fee-460dd0bd870d creating container for instance 2d51f058-cc9d-468f-bb69-5fb8790c465d
   Cell 5f4df484-e14b-4e86-8fee-460dd0bd870d successfully created container for instance 2d51f058-cc9d-468f-bb69-5fb8790c465d
   Staging...
   Staging process started ...
   Staging process finished
   Exit status 0
   Staging Complete
   Cell 5f4df484-e14b-4e86-8fee-460dd0bd870d stopping instance 2d51f058-cc9d-468f-bb69-5fb8790c465d
   Cell 5f4df484-e14b-4e86-8fee-460dd0bd870d destroying container for instance 2d51f058-cc9d-468f-bb69-5fb8790c465d
   Cell 5f4df484-e14b-4e86-8fee-460dd0bd870d successfully destroyed container for instance 2d51f058-cc9d-468f-bb69-5fb8790c465d

Waiting for app to start...

name:              Code-Think-NodeRED
requested state:   started
routes:            code-think-nodered-friendly-nyala.eu-gb.mybluemix.net
last uploaded:     Tue 06 Oct 17:16:24 BST 2020
stack:
docker image:      nodered/node-red:1.1.3-10-amd64

type:            web
instances:       1/1
memory usage:    256M
start command:   npm start --cache /data/.npm -- --userDir /data
     state     since                  cpu    memory          disk           details
#0   running   2020-10-06T16:16:52Z   0.0%   77.4M of 256M   433.1M of 1G
```

2. You can open your IBM Cloud Dashboard to see the service running as well.

* In a browser, open IBM Cloud and **select the dashboard icon** and **click on Cloud Foundry apps**.![View service.](img/DashboardServices.png)

* Click on your service from the list like the image shown below. ![Cloud Foundry app.](img/NodeRedCFService.png)

3. To access Node-RED, select **Visit App URL** from the service details page. ![Click Visit App URL.](img/AppURL.png)

You are now setup and ready for the next section!



### Option 2: Node-RED starter app on IBM Cloud

**Pre-requisites**

* Create an IBM Cloud account: [https://www.ibm.com/uk-en/cloud/free](https://www.ibm.com/uk-en/cloud/free)

1. From the IBM Cloud page, select in the upper menu options **Catalog**.![Select Catalog.](img/SelectCatalog.png)

2. In the search field type in **"Node Red"** and select the **Node-RED App**.![Select Node-RED App.](img/SearchNodeRed.png)

3. Click the **Get started** button to begin creating your Node-RED App.![Click on Get started.](img/GetStarted.png)

4. Change the *App Name** to something unique like `NodeREDCodeAtThinkXXX` where XXX are your initials.

5. **Important*** Make sure you select the **Lite** pricing plan. This is the free version.![Select the Lite pricing plan.](img/AppDetails.png)

6. Click the **Create** button to create the app. This may take up to 30 seconds.


7. Look for and click the blue button **Deploy your app**. ![Click Deploy your app.](img/DeployApp.png)

8. To configure your Node-RED app, complete the following:
 	* For this app, you'll need to create an API key. To do this, select the blue button **New** next to the field **API key** is needed. A popup will appear. 
	* Now select **Create**.![Create Node-RED app](img/CreateAPI.png)
	
9. Towards the top of the page, select the **Cloud Foundry** square. ![Select Cloud Foundry.](img/SelectCloudFoundry.png)

10. Select your **Region** attached to your account. This is probably London if you're in the UK. Use the pull down menu to select the proper region. If you don't know which one to use, select them until the red errors dissapear. A host name will be generated. You can modify the host name if you'd like.![Select your region.](img/SelectRegion.png)

11. Press **Next** and **Create** to finish setting up the Node-RED app. 
![Select Next and Create to finish the setup.](img/SelectNext.png)


	**Note:** We have created an Node Red app as well as a place in the Cloud where we can run the app on. Now the app will be deployed automatically. This can take up to 5 minutes. You can monitor the progess in the status field. Wait until the status changes from **In progress** to **Success**.
	![](img/DeploymentProgress.png)



12. Click on the name of your app under **Delivery Pipelines**.
![](img/DeploymentSuccess.png)

13. You have created the Node-Red app and you have deployed it in the IBM Cloud. Now, to go to your app select **View console**. ![](img/DeliveryPipeline.png)

14. Now you see the dashboard of your Node-Red app. Now select **Visit app URL**.![](img/AppDashboard.png)

15. Now you are in your Node-Red app. When opening this the first time you will get some options to set an User ID and Password. Follow the steps until you get the Node-Red landing page with the button **Go to your Node-RED flow editor**.
![](img/NodeRedFirstTime.png)

You are now setup and ready for the next section!

## Work in Node-RED
In this section, we will install the additional Node-RED nodes we need for our website and then import a flow that has been configured to communicate with z/OS.

### Install additional nodes

1. Open the hamburger menu on the upper right corner(1). This opens a menu like the one shown below. Choose the option **Manage palette** (2). ![Select Manage palette.](img/ManagePalette.png)

	Note: Manage Palette opens a screen where you can find all the Nodes which are installed and an option to search and install additional Nodes.

2. Select the **Install** tab. In the search field, type `dashboard`. This gives you all the nodes and node collections available with the name dashboard. Select the one called **Node-Red-Dashboard**. Select **Install** to the right of it to install the nodes. ![Install dashboard nodes.](img/InstallDashboardNode.png)


	**Note:** Some additional Nodes are being installed. This may take up to one minute. Please note that in some occasions a red error will occur saying that the installation has failed. You need to try again until you get a large green message that the installation was successful. This is a bug which can happen sometimes depending on your location.

3. Close the menu and return to the main screen. Inspect the tool tray on the left side
of the screen and look for the nodes installed under **dashboard** . ![](img/DashboardNodes.png)

	**Note:** The Dashboard Nodes are being used to build a graphical screen which you can use to interact. This will be our website. I have created the example website for you which uses these nodes.

### Import existing code

The next step is to import the example website so you do not have to build it
yourself from scratch. . . here we go!


1. Copy in the pre-created flow by copying the text in the link [https://raw.githubusercontent.com/SweetJenn23/Code-ThinkzOSAPI/main/NodeRedFlow](https://raw.githubusercontent.com/SweetJenn23/Code-ThinkzOSAPI/main/NodeRedFlow).


2. Go back to your Node-RED environment and select the hamburger menu on the upper right corner.Select **Import**. This opens a screen where you can paste the code. You will see the code appearing in the pink colored middle section.![](img/ImportFlow.png)

3. Press **Import**.

4. In the upper right hand corner, select the **Deploy** button to save and activate the flow.
![](img/FlowDeploy.png)

5. To see our dashboard website, we will need to open another browser or tab in a browser. To do this, in the tray on the right side, we will select the **Dashboard** icon. In the Dashboard tray, there is a Share or Open link icon in the top right corner. Click the **Open link** icon. ![](img/DashboardUI.png)

Let's try out our work!

### Making API calls to z/OS from containers

1. Go to the browser tab that shows your Node-RED flow. We are going to add a couple of nodes to make sure our API is working and understand what is happening.![Open your Node-RED flow.](img/Flow.png)

2. Open the the **http request** node next to *Show Catalog items*. Review the URL to make sure it matches the image below. Select **Done**. ![Review the HTTP details.](img/ShowCatalogItemsHTTP.png)

3. Open the **http request** node next to the *Enter item to search for* node. Review the URL and all other details to make sure it matches the image below. Select **Done**. ![Review the HTTTP details.](img/SearchHTTP.png)

4. To test our flow, we will add in a **Debug** node and **Inject** node. You can find the nodes by expanding the *Common* tray on the left hand side. They are the first two nodes listed.![Find the nodes.](img/Nodes.png)

5. Drag a **Debug** and **Inject** node onto your flow. Connect the **Inject** node to the left side or input side of the first **http request** node by clicking on the **Inject** node output terminal and dragging to the input terminal of **http request**. Connect the **Debug** node to the right side or the output side of the same **http request** node. Click **Deploy** to save and activate the flow. ![Insert and connect the Debug and Inject nodes.](img/NewNodes.png)

6. Select the gray box on the left side of the **Inject** node to manually call the API defined in the HTTP node. Select the **Debug** icon in the tray on the right side to see the output from the **Debug** node.![Inject data to call the API.](img/Inject.png)
	**Note:** The content of the message shown in debug isn't very pretty! That is exactly what Node-RED is getting back from z/OS through the API call. This isn't particularly useful.
	
7. In the left had tool tray, expand the **parser** section and hover over the **JSON** node. Node-RED comes with a node that can help us out! Notice that the **JSON** node is already in your flow.![Hover over JSON node.](img/Parser.png)

8. Delete the connection between your **Debug** node and the **http request** node by clicking on the line and pressing your **Delete** key. Create a connection between the **Debug** node input terminal (left side) and output ternminal (right side) of the **JSON** node by clicking on the input terminal of **Debug** and dragging to the output terminal of **JSON**. Click **Deploy**. ![Connect the Debug node to the JSON node.](img/JSONDebug.png)

9. Once again, the select the gray box on the left side of the **Inject** node to manually call the API. This time in the **Debug** tray, you'll see what the output looks like after it has been passed through the JSON node.![View the parsed JSON.](img/ParsedJSON.png)

10. This still isn't overly helpful as far as readability. Once again, Node-RED has a helpful **template** node to help us organize the data. Double click on the **orange template** node in your flow. In this node, you'll see that we've created a table using the `<table>` tag. We then check to see if particular fields are returned in the JSON that we are interested in using the `{{#<fieldname>}}{{/<fieldname>}}`. We also created a table row with data using `<tr><td></td></tr>`. Click **Done**.![](img/OrangeTemplate.png)

11. Delete the connection from the **JSON** node to the **Debug** node by clicking on it and using your **Delete** key. We will now connect the input terminal of the **Debug** node to the output terminal of the orange **template** node. Click **Deploy** to save and activate your changes. ![](img/TemplateDebug.png)

12. Once again, we will use our **Inject** node to see the output from **Debug**. Click the gray square on the left side of the **Inject** node. Review the **Debug** output on the rightside. This will be much more useful! ![](img/TemplateOutput.png)

	**Note:** We have now gone through all of the steps to work with the API response in Node-RED. Because we know what the responses will look like, we can use the same **JSON** and **template** nodes to parse and display the data for both API requests.
	
13. Double click on the blue **template** node. This is a Dashboard template that allows us to display the data to the dashboard UI. We are using a simple line of HTML to display the data and have selected to allow input to be passed through. Click **Done**. ![](img/Dashboard template.png)

14. Find your Dashboard UI open in another browser tab. Click the **Show Catalog Items** button. This button initiates an API call to CICS running on z/OS to find out which items are instock. This will show our pretty display from the prior steps.![Click Show Catalog Items.](img/ShowCatalogItems.png)

15. We can also search for a specific item. When we hit enter after typing in something to search for, this makes an API Get call to CICS to search for particular item. In the text field, type in `Paper` and hit **Enter** on your keyboard. **Note:** Capitalization does matter when searching. This is the second API in action but still using the same nodes to display the information. ![Search for an item.](img/Search.png)


Congratulations! You've now worked with an API in a container talking to applications running on z/OS!


