---
title: S’authentifier avec les bibliothèques Azure pour .NET
description: S’authentifier dans les bibliothèques Azure pour .NET
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072150"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="3e92b-103">S’authentifier avec les bibliothèques Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="3e92b-103">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="3e92b-104">Se connecter aux services avec des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="3e92b-104">Connect to services with connection strings</span></span>

<span data-ttu-id="3e92b-105">L’authentification avec la plupart des bibliothèques de service Azure nécessite une chaîne de connexion ou des clés.</span><span class="sxs-lookup"><span data-stu-id="3e92b-105">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="3e92b-106">Par exemple, SQL Database se sert d’une chaîne de connexion SQL standard :</span><span class="sxs-lookup"><span data-stu-id="3e92b-106">For example, SQL Database uses a standard SQL connection string:</span></span>

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;

using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

<span data-ttu-id="3e92b-107">Le stockage Azure utilise une clé de stockage :</span><span class="sxs-lookup"><span data-stu-id="3e92b-107">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="3e92b-108">Les chaînes de connexion de service sont utilisées dans d’autres services Azure tels que [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure cache for redims](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)et [service bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="3e92b-108">Service connection strings are used in other Azure services like [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="3e92b-109">Vous pouvez récupérer ces chaînes à l’aide de l’Portail Azure, de l’interface CLI ou de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e92b-109">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="3e92b-110">Vous pouvez aussi utiliser les bibliothèques de gestion Azure pour .NET pour interroger des ressources et générer des chaînes de connexion dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3e92b-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="3e92b-111">Par exemple, cet extrait de code utilise les bibliothèques de gestion pour créer une chaîne de connexion de compte de stockage :</span><span class="sxs-lookup"><span data-stu-id="3e92b-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

<span data-ttu-id="3e92b-112">D’autres bibliothèques ont besoin que votre application s’exécute avec un [principal de service](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) qui l’autorise à s’exécuter avec des informations d’identification accordées.</span><span class="sxs-lookup"><span data-stu-id="3e92b-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="3e92b-113">Cette configuration est similaire à celle de l’authentification basée sur un objet pour les bibliothèques de gestion répertoriées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3e92b-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a><span data-ttu-id="3e92b-114">Authentification des bibliothèques de gestion Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="3e92b-114">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](../includes/create-sp.md)]

<span data-ttu-id="3e92b-115">Une fois le principal de service créé, vous disposez de deux options pour vous authentifier au principal de service et créer et gérer les ressources.</span><span class="sxs-lookup"><span data-stu-id="3e92b-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="3e92b-116">Pour les deux options, vous devez ajouter les packages NuGet suivants à votre projet.</span><span class="sxs-lookup"><span data-stu-id="3e92b-116">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="3e92b-117">S’authentifier à l’aide d’informations d’identification de jeton</span><span class="sxs-lookup"><span data-stu-id="3e92b-117">Authenticate with token credentials</span></span>

<span data-ttu-id="3e92b-118">La première méthode consiste à générer l’objet d’informations d’identification de jeton sous forme de code.</span><span class="sxs-lookup"><span data-stu-id="3e92b-118">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="3e92b-119">Vous devez stocker les informations d’identification en sécurité dans un fichier de configuration, dans le registre ou dans Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="3e92b-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="3e92b-120">Utilisez les valeurs *clientId*, *clientSecret* et *tenantId* de la sortie JSON obtenue à la création du principal de service.</span><span class="sxs-lookup"><span data-stu-id="3e92b-120">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="3e92b-121">Créez ensuite l’objet de point d’entrée `Azure` pour commencer à utiliser les API :</span><span class="sxs-lookup"><span data-stu-id="3e92b-121">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="3e92b-122">Authentification basée sur un fichier</span><span class="sxs-lookup"><span data-stu-id="3e92b-122">File-based authentication</span></span>

<span data-ttu-id="3e92b-123">L’authentification basée sur un fichier vous permet de placer les informations d’identification du principal de service dans un fichier texte brut et de les sécuriser dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3e92b-123">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](../includes/file-based-auth.md)]

<span data-ttu-id="3e92b-124">Lisez le contenu du fichier puis créez l’objet de point d’entrée `Azure` pour commencer à utiliser les API :</span><span class="sxs-lookup"><span data-stu-id="3e92b-124">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```