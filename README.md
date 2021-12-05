<h1 align="center" style="border-bottom: none;">🔎 Natural Language Understanding Code Pattern </h1>
<h3 align="center">Natural Language Understanding is a collection of APIs that offer text analysis through natural language processing. This set of APIs can analyze text to help you understand its concepts, entities, keywords, sentiment, and more. Additionally, you can create a custom model for some APIs to get specific results that are tailored to your domain.</h3>
<p align="center">
  <a href="https://github.com/IBM/natural-language-understanding-code-pattern/actions/workflows/nodejs.yml/">
    <img alt="GitHub Actions" src="https://github.com/IBM/natural-language-understanding-code-pattern/actions/workflows/nodejs.yml/badge.svg?branch=master">
  </a>
  <a href="#badge">
    <img alt="semantic-release" src="https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg">
  </a>
</p>
</p>

Demo: [https://natural-language-understanding-code-pattern.ng.bluemix.net/](https://natural-language-understanding-code-pattern.ng.bluemix.net/)

### Flow

<p align="center">
  <img alt="architecture" width="600" src="./public/architecture.png">
</p>

1. User sends messages to the application (running locally, in the IBM Cloud or in IBM Cloud Pak for Data).
1. The application sends the user message to IBM Watson Natural Language Understanding service.
1. Watson Natural Language Understanding processes the text or url and extract features such us keywords, concepts, categories. The service can be provisioned on either IBM Cloud or IBM Cloud Pak for Data.

<h3>BADM-4830</h3>
</p>

1. login to the development virtual machine VM hosted on AWS cloud

	 `
    ssh ubuntu@XX.XXX.XXX.XXX
    `
    
    *Make sure to post your **ssh public key** to the Watson studio project used for this lesson
    
2. Navigate to class subdirectory

	`cd /home/ubuntu/4830`
3. Create & navigate to your own directory

	`mkdir userName`
	
	`cd userName`
	
	For example:
	
	`mkdir ivanp`
	
	`cd ivanp`
	
	
4. Clone NLU repository from github

	`git clone https://github.com/BADM-4830/natural-language-understanding-code-pattern.git`
	
5. Change directory to NLU directory

	`cd natural-language-understanding-code-pattern/`
6. Create `.env` file with:

	`cp .env.example .env`
7. Remember to update the following configuration variables in `.env` once you have created your `Watson NLU` instance on the IBM cloud.

```
	NATURAL_LANGUAGE_UNDERSTANDING_APIKEY=<COPY-YOUR-API-KEY-HERE>
	NATURAL_LANGUAGE_UNDERSTANDING_URL=https://api.us-south.natural-language-understanding.watson.cloud.ibm.com/instances/*********
	PORT=5001
```







### Manual deployment

The recommended approach is to download the credentials file and place it in the directory where you code is. Follow the following steps only if you want to manually configure your authentication mechanism.


Configure the authentication manually

1.  In the application folder, copy the _.env.example_ file and create a file called _.env_

    ```
    cp .env.example .env
    ```

2.  Open the _.env_ file and add the service credentials depending on your environment.

    Example _.env_ file that configures the `apikey` and `url` for a Natural Language Understanding service instance hosted in the US South region:

    ```
    NATURAL_LANGUAGE_UNDERSTANDING_IAM_APIKEY=X4rbi8vwZmKpXfowaS3GAsA7vdy17Qh7km5D6EzKLHL2
    NATURAL_LANGUAGE_UNDERSTANDING_URL=https://api.us-south.natural-language-understanding.watson.cloud.ibm.com/instances/XXXXXXXX
    PORT=XXXX
    ```



## Running locally

1. Install the dependencies

   ```
   npm install
   ```

1. Build the application

   ```
   npm run build
   ```

1. Run the application

   ```
   npm run dev
   ```

1. View the application in a browser at `XX.XXX.XXX.XXX:PORT`

where `XX.XXX.XXX.XXX` is the IP we used in the login step above and `PORT` is the port number provided in the `.env` file earlier.

## Deploying to IBM Cloud as a Cloud Foundry Application


### Manually

1. Build the application

   ```
   npm run build
   ```

1. Login to IBM Cloud with the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview)

   ```
   ibmcloud login
   ```

1. Target a Cloud Foundry organization and space & Target a Resource Group with

   ```
   ibmcloud target --cf
   ibmcloud target -g Default
   ```

1. Edit the _manifest.yml_ file. Change the **name** field to something unique. For example, 

	`- name: my-app-name`
	
2. Edit the _manifest.yml_ file. Change the **buildpacks** field to:

	``` 
		buildpacks:
      		- nodejs_buildpack
    ```
1. Deploy the application

   ```
   ibmcloud app push
   ```

1. View the application online at the app URL, for example: https://my-app-name.mybluemix.net

## Prerequisites

### Public Cloud

1. Sign up for an [IBM Cloud account](https://console.bluemix.net/registration/).
1. Download the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview).
1. Create an instance of the Natural Language Understanding service and get your credentials:
   - Go to the [Natural Language Understanding](https://console.bluemix.net/catalog/services/natural-language-understanding) page in the IBM Cloud Catalog.
   - Log in to your IBM Cloud account.
   - Click **Create**.
   - Click **Show** to view the service credentials.
   - Copy the `apikey` value.
   - Copy the `url` value.





## Directory structure

```none
.
├── app.js                      // express routes
├── config                      // express configuration
│   ├── error-handler.js
│   ├── express.js
│   └── security.js
├── package.json
├── openshift                   // openshift template
├── public                      // static resources
├── server.js                   // entry point
├── test                        // integration tests
└── src                         // react client
    ├── __test__                // unit tests
    └── index.js                // app entry point
```

## License

This sample code is licensed under the [MIT License](https://opensource.org/licenses/MIT).

## Open Source @ IBM

Find more open source projects on the [IBM Github Page](http://ibm.github.io/)

