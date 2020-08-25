---
title: Fonctionnement de l’authentification dans les bibliothèques Azure pour .NET
description: Explique les différentes façons de s’authentifier avec le kit de développement logiciel (SDK) Azure pour .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: bc2fce919d88a528f21df9f561cbe33e1119762a
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811377"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a>S’authentifier avec le kit de développement logiciel (SDK) Azure pour .NET

## <a name="recommended-azureidentity"></a>Recommandé : Azure. Identity

Les derniers packages du kit de développement logiciel (SDK) Azure pour .NET utilisent un package d’authentification commun pour l’authentification `Azure.Identity` . L’utilisation `Azure.Identity` de est recommandée par rapport à d’autres mécanismes d’authentification décrits plus loin dans ce document. Les packages prenant en charge les informations d’identification fournies par `Azure.Identity` sont basés sur `Azure.Core` et ont des identificateurs de package commençant par *Azure*. [Consultez la liste](packages.md) des packages pour un inventaire des packages qui utilisent `Azure.Core` .

Pour obtenir des instructions complètes sur l’utilisation `Azure.Identity` de dans votre projet, consultez la documentation relative à [Azure Identity client pour .net](/dotnet/api/overview/azure/identity-readme).

> [!TIP]
> Pour obtenir des exemples d’utilisation de l’identité Azure pour gérer et accéder aux ressources Azure, consultez l’exemple d’identité [, de gestion des ressources et de stockage Azure](/samples/dotnet/samples/azure-identity-resource-management-storage/) .

Pour vous authentifier avec les bibliothèques qui ne prennent pas en charge Azure. Identity, consultez le reste de cette rubrique.

## <a name="access-azure-resources"></a>Accéder aux ressources Azure

Pour interagir avec des ressources Azure, telles que la récupération d’un secret à partir d’Key Vault ou le stockage d’un objet BLOB dans le stockage, de nombreuses bibliothèques de service Azure nécessitent une chaîne de connexion ou des clés pour l’authentification. Par exemple, SQL Database utilise une [chaîne de connexion SQL standard](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core). Les chaînes de connexion de service sont utilisées dans d’autres services Azure tels que [CosmosDB](/azure/cosmos-db/), [Azure cache for redims](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)et [service bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Vous pouvez récupérer ces chaînes à l’aide de l’Portail Azure, de l’interface CLI ou de PowerShell. Vous pouvez aussi utiliser les bibliothèques de gestion Azure pour .NET pour interroger des ressources et générer des chaînes de connexion dans votre code.

Les méthodes d’utilisation d’une chaîne de connexion varient en fonction du produit. [Reportez-vous à la documentation de votre produit Azure](/azure/?product=featured).

## <a name="manage-azure-resources"></a>Gérer des ressources Azure

[!include[Create service principal](includes/create-sp.md)]

Une fois le principal de service créé, vous disposez de deux options pour vous authentifier au principal de service et créer et gérer les ressources.

Pour les deux options, vous devez ajouter les packages NuGet suivants à votre projet.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>S’authentifier à l’aide d’informations d’identification de jeton

La première méthode consiste à générer l’objet d’informations d’identification de jeton sous forme de code. Vous devez stocker les informations d’identification en sécurité dans un fichier de configuration, dans le registre ou dans Azure Key Vault.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

Utilisez les valeurs *clientId*, *clientSecret* et *tenantId* de la sortie JSON obtenue à la création du principal de service.

Créez ensuite l’objet de point d’entrée `Azure` pour commencer à utiliser les API :

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

Il est recommandé de fournir explicitement le *SubscriptionId* à partir de la sortie JSON vers l' `Azure` objet :

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Authentification basée sur un fichier

L’authentification basée sur un fichier vous permet de placer les informations d’identification du principal de service dans un fichier texte brut et de les sécuriser dans le système de fichiers.

[!include[File-based authentication](includes/file-based-auth.md)]

Lisez le contenu du fichier puis créez l’objet de point d’entrée `Azure` pour commencer à utiliser les API :

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
