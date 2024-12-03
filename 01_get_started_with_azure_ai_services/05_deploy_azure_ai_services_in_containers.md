# Deploy Azure AI services in containers

Learning objectives

After completing this module, learners will be able to:

- Create containers for reuse
- Deploy to a container and secure a container
- Consume Azure AI services from a container


## Intro

Containers enable you to host Azure AI services either on-premises or in Azure. For example, if your application uses sensitive data in an on-premises SQL Server to call an Azure AI services service, you can deploy Azure AI services in containers on the same network.

## Understand containers

### Container deployment

To use a container, you typically pull the container image from a registry and deploy it to a container host, specifying any required configuration settings. The container host can be in the cloud, in a private network, or on your local computer. For example:

- A Docker* server.
- An Azure Container Instance (ACI).
- An Azure Kubernetes Service (AKS) cluster.


## Use Azure AI services containers

There are container images for Azure AI services in the Microsoft Container Registry that you can use to deploy a containerized service that encapsulates an individual Azure AI services service API.
To deploy and use an Azure AI services container, the following three activities must occur:

1. The container image for the specific Azure AI services API you want to use is downloaded and deployed to a container host, such as a local Docker server, an Azure Container Instance (ACI), or Azure Kubernetes Service (AKS).
2. Client applications submit data to the endpoint provided by the containerized service, and retrieve results just as they would from an Azure AI services cloud resource in Azure.
3. Periodically, usage metrics for the containerized service are sent to an Azure AI services resource in Azure in order to calculate billing for the service.

Even when using a container, you must provision an Azure AI services resource in Azure for billing purposes. Client applications send their requests to the containerized service, meaning that potentially sensitive data is not sent to the Azure AI services endpoint in Azure; but the container must be able to connect to the Azure AI services resource in Azure periodically to send usage metrics for billing.


### Azure AI services container images

Each container provides a subset of Azure AI services functionality. For example, not all features of the Azure AI Language service are in a single container. Language detection, translation, and sentiment analysis are each separate container images.

For a full list of currently available Azure AI services container images, and specific notes for each one, see [Azure AI services container image tags and release notes](https://learn.microsoft.com/en-us/azure/ai-services/cognitive-services-container-support#containers-in-azure-ai-services).

### Azure AI services container configuration

When you deploy an Azure AI services container image to a host, you must specify three settings.
- ApiKey: 	Key from your deployed Azure AI service; used for billing.
- Billing: 	Endpoint URI from your deployed Azure AI service; used for billing.
- Eula: 	Value of accept to state you accept the license for the container.

### Consuming Azure AI services from a Container

After your Azure AI services container is deployed, applications consume the containerized Azure AI services endpoint rather than the default Azure endpoint. 

The client application must be configured with the appropriate endpoint for your container, but does not need to provide a subscription key to be authenticated. 

You can implement your own authentication solution and apply network security restrictions as appropriate for your specific application scenario.

## Exercise - Use an Azure AI Services Container

https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/04-use-a-container.html