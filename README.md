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

* You should now see your service running like the image shown below. ![Cloud Foundry app.](img/NodeRedCFService.png)



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

15. Now you are in your Node-Red app. When opening this the first time you will get some options to set an User ID and Password. Follow the steps until you get the Node-Red landing page with the button **Go to your Node-RED editor**.
![](img/NodeRedFirstTime.png)


