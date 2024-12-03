# Create and Consume Azure AI Services

### Learning objectives

After completing this module, you'll able to:

- Create Azure AI services resources in an Azure subscription
- Identify endpoints, keys, and locations required to consume an Azure AI services resource.
- Use a REST API and an SDK to consume Azure AI services.

AI services are out-of-the-box solutions for common AI scenarios. A few examples of individual Azure AI services include:

- Azure AI Vision - Analyze content in images and videos.
- Azure AI Language - Build apps with industry-leading natural language understanding capabilities.
- Azure AI Speech - Speech to text, text to speech, translation, and speaker recognition.
- Azure AI Document Intelligence - An optical character recognition (OCR) solution that can extract semantic meaning from forms, such as invoices, receipts, and others.
- Azure AI Search - A cloud-scale search solution that uses AI services to extract insights from data and documents.
- Azure OpenAI - An Azure AI service that provides access to the capabilities of OpenAI GPT-4.

The approach to provisioning and consuming them is generally the same for all services.

## Provision an Azure AI services resource

To use any of the AI services, you need to create appropriate resources in an Azure subscription.

### Options for Azure resources

 You can choose between the following provisioning options:

 - **Multi-service resource**: resource that supports multiple different AI services e.g. the Azure AI Language, Azure AI Vision, Azure AI Speech. This approach enables you to manage a single set of access credentials to consume multiple services at a single endpoint, and with a single point of billing 
 - **Single-service resource**: Each AI service can be provisioned individually. This approach enables you to use separate endpoints for each service (for example to provision them in different geographical regions) and to manage access credentials & billing for each service independently.
- **Training and Prediction resources**: While most AI services can be used through a single Azure resource, some offer (or require) separate resources for model training and prediction.

## Identify endpoints and keys

To consume the service through the endpoint, applications require the following information:

- The endpoint URI. This is the HTTP address at which the REST interface for the service can be accessed.
- A subscription key. Client applications must provide a valid key to consume the service. Two keys are created - applications can use either key.
- The resource location. A resource in Azure is generally assigned it to a location, which determines the Azure data center in which the resource is defined. While most SDKs use the endpoint URI to connect to the service, some require the location.

## Using REST Apis and SDKs

SDK availability varies by individual AI services, but for most services there's an SDK for languages such as:
- Microsoft C# (.NET Core)
- Python
- JavaScript (Node.js)
- Go
- Java

## Exercise - Use Azure AI services

- I created a Resource Group
- In the Resource Group, I created a Multi-Service AI resource
- After creating and deploying the resourcez, Azure generates keys and endpoints for the resource which can be used with REST API or SDK to consume the service.

