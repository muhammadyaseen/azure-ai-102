# Secure Azure AI services

### Learning objectives

After completing this module, you will know how to:

- Consider authentication for Azure AI services
- Manage network security for Azure AI services

Azure AI services provides multiple layers of security that you should consider when implementing a solution.

By default, access to Azure AI services resources is restricted by using subscription keys. Management of access to these keys is a primary consideration for security.


# Unit 02: Consider Authentication

## Regenerate keys

Each AI service is provided with two keys, enabling you to regenerate keys without service interruption e.g. in a Red / Blue deployment scenario.

## Protect keys with Azure Key Vault

Azure Key Vault is an Azure service in which you can securely store secrets (such as passwords and keys). Access to the key vault is granted to "security principals".

Administrators can assign a security principal to an application (also known as a service principal) to define a managed identity for the application. 

The application can then use this identity to access the key vault and retrieve a secret to which it has access e.g. subscription keys for an AI services resource. This minimizes the risk of it being compromised by being hard-coded in an application or saved in a configuration file.

## Token-based authentication

When using the REST interface, some AI services support (or even require) token-based authentication where a subscription key is presented in an initial request to obtain an authentication token with a validity period of 10 minutes. Subsequent requests must present the token to validate that the caller has been authenticated.

## Microsoft Entra ID authentication

Azure AI services supports Microsoft Entra ID authentication, enabling you to grant access to specific service principals or managed identities for apps and services running in Azure. There are different ways you can authenticate against Azure AI services using Microsoft Entra ID, including:

- Authenticate using service principals
- Authenticate using managed identities
    - User-assigned managed identities: are created to be useable by multiple resources instead of being tied to one. It exists independently of any single resource.
    - System-assigned managed identities:  are created and linked to a specific resource, such as a virtual machine that needs to access Azure AI services. When the resource is deleted, the identity is deleted as well.

You can assign each type of managed identity to a resource either during creation of the resource, or after it has already been created.

# Unit 03: Implement Network Security

## Apply network access restrictions

By default, Azure AI services are accessible from all networks. Some individual AI services resources (such as Azure AI Face service, Azure AI Vision, and others) can be configured to restrict access to specific network addresses - either public Internet addresses or addresses on virtual networks.

With network restrictions enabled, a client trying to connect from an IP address that isn't allowed will receive an Access Denied error.

## Unit 04: Exercise - Manage Azure AI Services Security

A better approach when developing applications on Azure is to store the key securely in Azure Key Vault, and provide access to the key through a managed identity (in other words, a user account used by the application itself)

To access the secret in the key vault, your application must use a service principal that has access to the secret. You'll use the Azure command line interface (CLI) to create the service principal, find its object ID, and grant access to the secret in Azure Vault.

https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/02-ai-services-security.html