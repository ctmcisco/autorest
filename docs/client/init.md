# Initialization
AutoRest generates a client type based on command-line inputs and the specification (see [Defining Clients with Swagger](../developer/guide/how-autorest-generates-code-from-swagger.md). The generated client inherits from the [ServiceClient<T>](https://github.com/Azure/azure-sdk-for-net/blob/psSdkJson6/src/SdkCommon/ClientRuntime/ClientRuntime/ServiceClient.cs) base type which is in the *Microsoft.Rest.ClientRuntime* nuget package. 

The client type has several  constructors: 
## Default Constructor
The default constructor sets the Base URL of the client to the value provided in the specification.  The client is configured to use anonymous authentication.
```csharp
var myClient = new SwaggerPetstore();
```
## Constructor with Base URL
The default Base URL from the specification can be overridden by passing a new URL when instantiating the client.
```csharp
var myClient = new SwaggerPetstore(new Uri("https://contoso.org/myclient"));
```
## Constructor with Credentials
* Clients generated with the AddCredentials flag have a *Credentials* property and a constructor that accepts a Credentials object (see [Authentication](auth.md))
```csharp
var myClient = new SwaggerPetstore(new BasicAuthenticationCredentials
	{
		UserName = "ContosoUser",
		Password = "P@$$w0rd"
	});
```
## Constructor with Delegating Handlers
The generated client includes a constructor that includes all the optional parameters from above and a collection of delegating handlers
```csharp
var myClient = new SwaggerPetstore(new MyCustomDelegatingHandler());
```
