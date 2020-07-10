---
title: Fonctionnement de l’authentification dans les bibliothèques Azure pour .NET
description: Explique les différentes façons de s’authentifier avec le kit de développement logiciel (SDK) Azure pour .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 5ed29d5485dc7f59bcc757c8903116edf6bd5d7d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174944"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="6c0c8-103">S’authentifier avec le kit de développement logiciel (SDK) Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="6c0c8-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="6c0c8-104">Recommandé : Azure. Identity</span><span class="sxs-lookup"><span data-stu-id="6c0c8-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="6c0c8-105">Les derniers packages du kit de développement logiciel (SDK) Azure pour .NET utilisent un package d’authentification commun pour l’authentification `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="6c0c8-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="6c0c8-106">L’utilisation `Azure.Identity` de est recommandée par rapport à d’autres mécanismes d’authentification décrits plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="6c0c8-107">Les packages prenant en charge les informations d’identification fournies par `Azure.Identity` ont des identificateurs de package commençant par *Azure.*</span><span class="sxs-lookup"><span data-stu-id="6c0c8-107">Packages supporting the credentials provided by `Azure.Identity` have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="6c0c8-108">[Pour plus d’informations, consultez les dernières versions du kit de développement logiciel (SDK) Azure pour .net](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span><span class="sxs-lookup"><span data-stu-id="6c0c8-108">[For more information, see the latest releases in the Azure SDK for .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span></span>

<span data-ttu-id="6c0c8-109">Pour obtenir des instructions complètes sur l’utilisation `Azure.Identity` de dans votre projet, consultez la documentation relative à [Azure Identity client pour .net](/dotnet/api/overview/azure/identity-readme).</span><span class="sxs-lookup"><span data-stu-id="6c0c8-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="6c0c8-110">Pour obtenir des exemples d’utilisation de l’identité Azure pour gérer et accéder aux ressources Azure, consultez l’exemple d’identité [, de gestion des ressources et de stockage Azure](/samples/dotnet/samples/azure-identity-resource-management-storage/) .</span><span class="sxs-lookup"><span data-stu-id="6c0c8-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="6c0c8-111">Pour vous authentifier avec les bibliothèques qui ne prennent pas en charge Azure. Identity, consultez le reste de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="6c0c8-112">Accéder aux ressources Azure</span><span class="sxs-lookup"><span data-stu-id="6c0c8-112">Access Azure resources</span></span>

<span data-ttu-id="6c0c8-113">Pour interagir avec des ressources Azure, telles que la récupération d’un secret à partir d’Key Vault ou le stockage d’un objet BLOB dans le stockage, de nombreuses bibliothèques de service Azure nécessitent une chaîne de connexion ou des clés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="6c0c8-114">Par exemple, SQL Database utilise une [chaîne de connexion SQL standard](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6c0c8-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="6c0c8-115">Les chaînes de connexion de service sont utilisées dans d’autres services Azure tels que [CosmosDB](/azure/cosmos-db/), [Azure cache for redims](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)et [service bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="6c0c8-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="6c0c8-116">Vous pouvez récupérer ces chaînes à l’aide de l’Portail Azure, de l’interface CLI ou de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="6c0c8-117">Vous pouvez aussi utiliser les bibliothèques de gestion Azure pour .NET pour interroger des ressources et générer des chaînes de connexion dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="6c0c8-118">Les méthodes d’utilisation d’une chaîne de connexion varient en fonction du produit.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="6c0c8-119">[Reportez-vous à la documentation de votre produit Azure](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="6c0c8-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="6c0c8-120">Gérer des ressources Azure</span><span class="sxs-lookup"><span data-stu-id="6c0c8-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="6c0c8-121">Une fois le principal de service créé, vous disposez de deux options pour vous authentifier au principal de service et créer et gérer les ressources.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="6c0c8-122">Pour les deux options, vous devez ajouter les packages NuGet suivants à votre projet.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="6c0c8-123">S’authentifier à l’aide d’informations d’identification de jeton</span><span class="sxs-lookup"><span data-stu-id="6c0c8-123">Authenticate with token credentials</span></span>

<span data-ttu-id="6c0c8-124">La première méthode consiste à générer l’objet d’informations d’identification de jeton sous forme de code.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="6c0c8-125">Vous devez stocker les informations d’identification en sécurité dans un fichier de configuration, dans le registre ou dans Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="6c0c8-126">Utilisez les valeurs *clientId*, *clientSecret* et *tenantId* de la sortie JSON obtenue à la création du principal de service.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="6c0c8-127">Créez ensuite l’objet de point d’entrée `Azure` pour commencer à utiliser les API :</span><span class="sxs-lookup"><span data-stu-id="6c0c8-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="6c0c8-128">Authentification basée sur un fichier</span><span class="sxs-lookup"><span data-stu-id="6c0c8-128">File-based authentication</span></span>

<span data-ttu-id="6c0c8-129">L’authentification basée sur un fichier vous permet de placer les informations d’identification du principal de service dans un fichier texte brut et de les sécuriser dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6c0c8-129">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="6c0c8-130">Lisez le contenu du fichier puis créez l’objet de point d’entrée `Azure` pour commencer à utiliser les API :</span><span class="sxs-lookup"><span data-stu-id="6c0c8-130">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
