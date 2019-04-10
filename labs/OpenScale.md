# Machine Learning: Monitor WML model with Watson OpenScale

IBM Watson OpenScale is an open environment that enables organizations to automate and operationalize their AI. OpenScale provides a powerful platform for managing AI and ML models. Learn how to train, create and deploy a machine learning model using Jupyter Notebook and Watson Studio. Use OpenScale to log payload and monitor performance, quality, and fairness of the model. Some additional resources are below:

* [Watson OpenScale Documentation](https://cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-gettingstarted#gettingstarted)
* [Introduction Video](https://www.youtube.com/watch?v=udSKUkGANHA&t=2s)
* [IBM Developer Code Patterns for OpenScale](https://developer.ibm.com/?s=openscale&orderby=date&order=DESC&post_type%5B%5D=ibmcode_patterns)
* [Code Pattern for this lab](https://developer.ibm.com/patterns/monitor-performance-fairness-and-quality-of-a-wml-model-with-ai-openscale-apis/)

## Prerequisites

This lab will guide you through building a Spark ML based model to determine if an applicants credit risk. Some familiarity with Machine Learning will be useful in understanding the model, though not necessary as all the code is provided for you to build the credit risk model. Once the model is built, Watson OpenScale will be used to monitor the models fairness, performance and explain the results of transactions. To run through the lab, you will need:
* An IBM Cloud ID

## Instructions

In order to run the lab, you should go through the following steps to set up the Watson Studio environment where the Machine Learning model will be created.

1. Go to the [IBM Cloud console]((https://ibm.biz/Bd2WCn)) - (https://ibm.biz/Bd2WCn) and log in (or create an account if you do not have one).

1. Click on the **`Catalog`** link in the top banner of the IBM Cloud dashboard.  
   ![catalog-link](docs/images/1.png)

1. Select the AI category on the left, under `All Categories`.  
   ![ai-filter](docs/images/2.png)

1. Select the Watson OpenScale service tile.  
   ![ws-tile](docs/images/11.png)

1. Leave the default options and click the **`Create`** button.  
   NOTE: At this time (3/27/19) you must use an instance of Watson OpenScale deployed in the `Dallas` region. This is currently the only region that sends events about scoring requests to the message hub, which is read by OpenScale to populate the payload logging table.
   ![create-ws-instance](docs/images/12.png)

1. Still in the IBM Cloud console page, Click on the **`Catalog`** link in the top banner of the IBM Cloud dashboard.  

1. Select the 'AI' category on the left, under `All Categories`. Then select the 'Machine Learning' service tile.
   ![wml](docs/images/17.png)

1. Leave the default options, using the Lite plan and click the **`Create`** button.  
   ![create-wml-instance](docs/images/18.png)

1. Still in the IBM Cloud console page, Click on the **`Catalog`** link in the top banner of the IBM Cloud dashboard.  

1. Select the 'Storage' category on the left, under `All Categories`. Then select the 'Object Storage' service tile.
   ![cloud-cos](docs/images/6.png)

1. Leave the default options, using the Lite plan and click the **`Create`** button.  
   ![create-ws-instance](docs/images/7.png)

1. Still in the IBM Cloud console page, Click on the **`Catalog`** link in the top banner of the IBM Cloud dashboard.  

1. Select the AI category on the left, under `All Categories`.  
   ![ai-filter](docs/images/2.png)

1. Select the Watson Studio service tile.  
   ![ws-tile](docs/images/3.png)

1. Leave the default options and click the **`Create`** button.  
   ![create-ws-instance](docs/images/4.png)

1. On the service page. Right click on the **`Get Started`** button and select to open in a new tab to open the Watson Studio tooling.  
   ![ws-tooling](docs/images/5.png)

1. Gather the credentials & keys needed for the tutorial as outlined in the [credentials section below](#gathering-service-credentials-and-keys)

1. **You can now follow the instructions for the code pattern found at the following [git repo](https://github.com/jrtorres/monitor-wml-model-with-watson-openscale/blob/master/README.md) to complete this lab.**

### Gathering Service Credentials and Keys

* The tutorial uses an API key to authenticate against the IBM Cloud. If you have the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/reference/ibmcloud/download_cli.html#install_use) installed, your Cloud API key can be generated using the following commands:

   ```bash
   bx login --sso
   bx iam api-key-create 'my_key'
   ```

   If you do not have the CLI installed, you can use the web console to create and gather this API key:
   1. On the IBM Cloud comsole page (http://cloud.ibm.com), click on the `Manage` drop down menu on the top right and select the **`Access (IAM)`** link. 
      ![ws-tooling](docs/images/13.png)

   1. Click on the `IBM Cloud API keys` option on the left menu and click on the **`Create an IBM Cloud API key`** button.
      ![ws-tooling](docs/images/14.png)

   1. Give your key a name and click the `Create` button.
      ![ws-tooling](docs/images/15.png)

   1. Download and/or copy the key (It can not be retrieved later, so make sure you store this key).
      ![ws-tooling](docs/images/16.png)

* To get the Watson OpenScale GUID, we can either find the GUID from the IBM Cloud browser URL or by using the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/reference/ibmcloud/download_cli.html#install_use) with the following command (the <Watson_OpenScale_instance_name> you use is the name used when you provisioned the service):

   ```bash
   bx resource service-instance <Watson_OpenScale_instance_name>
   ```

   If you do not have the CLI installed, you can find the GUID in the browser url. When you open the Watson Open Scale service instance on the IBM Cloud page, you will see in the url a location where the service is deployed followed by two alphanumerics separated by a colon. The service GUID is the second alphanumeric (after the colon and followed by two colons)
   ![wos-url](docs/images/8.png)

* The tutorial uses Watson Machine Learning to deploy the ML model. In order to interact with the service, you need to get the service credentials. You can find this by going to the service page in the IBM Cloud console page. Click on the `Service Credentials` option on the left hand panel. If you do not have any credentials **Click** on the `New credentials` button and then click on the `Add` button. Copy these service credentials and save them for later.
   ![wml-url](docs/images/19.png)
   ![wml-creds](docs/images/20.png)

## Call to Action

Continue exploring Watson OpenScale and Watson Machine Learning through the following resources:
* https://github.com/pmservice/ai-openscale-tutorials/tree/master/notebooks

Join the 2019 Call for Code challenge today!
* https://developer.ibm.com/callforcode/
* https://developer.ibm.com/code-and-response/technologies/data-science

[Top](../README.md)