---
title: Applications sans serveur Azure Functions
description: Azure Functions offre des fonctionnalités sans serveur dans plusieursC#langues (, JavaScript, Java) et des plateformes pour fournir un code de mise à l’échelle instantanée piloté par les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920967"
---
# <a name="azure-functions"></a>Azure Functions

Azure Functions offre une expérience de calcul sans serveur. Une fonction est appelée par un *déclencheur* (comme l’accès à un point de terminaison http ou une minuterie) et exécute un bloc de code ou une logique métier. Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources telles que le stockage et les files d’attente.

![Logo Azure Functions](./media/azure-functions-logo.png)

Il existe deux versions de l’infrastructure Azure Functions. La version héritée prend en charge la .NET Framework complète et le nouveau Runtime prend en charge les applications .NET Core multiplateforme. Des langages C# supplémentaires, tels que F#JavaScript, et Java, sont pris en charge. Les fonctions créées dans le portail fournissent une syntaxe de script riche. Les fonctions créées en tant que projets autonomes peuvent être déployées avec une prise en charge complète des plateformes et des fonctionnalités.

Pour plus d’informations, consultez [la documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Fonctions v1 et v2

Il existe deux versions du Azure Functions Runtime : 1. x et 2. x. La version 1. x est généralement disponible (GA). Il prend en charge le développement .NET à partir du portail ou des ordinateurs Windows et utilise le .NET Framework. 1. x prend C#en charge, JavaScript F#et, avec prise en charge expérimentale de Python, php, machine à écrire, batch, bash et PowerShell.

La [version 2. x est également mis à la disposition générale dès maintenant](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Il s’appuie sur .NET Core et prend en charge le développement multiplateforme sur des ordinateurs Windows, macOS et Linux. 2. x ajoute une prise en charge de première classe pour Java, mais ne prend pas encore en charge directement les langages expérimentaux. La version 2. x utilise un nouveau modèle d’extensibilité de liaison qui active des extensions tierces à la plateforme, un contrôle de version indépendant des liaisons et un environnement d’exécution plus rationalisé.

> **Il existe un problème connu dans 1. x avec [la prise en charge de la redirection de liaison](https://github.com/Azure/azure-functions-host/issues/992).** Le problème est spécifique au développement .NET. Les projets avec des dépendances sur des bibliothèques qui sont une version différente des bibliothèques incluses dans le runtime sont affectés. L’équipe Functions s’est engagée à créer une progression concrète sur le problème. L’équipe traitera les redirections de liaison dans 2. x avant de passer à la mise à la disposition générale. La déclaration officielle de l’équipe avec des correctifs suggérés et des solutions de contournement est disponible ici : [résolution de l’assembly dans Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Pour plus d’informations, consultez [comparer 1. x et 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Prise en charge des langages de programmation

Les langues suivantes sont prises en charge dans General Availability (GA), preview ou expérimental.

|Language      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |DISPONIBLE          |Aperçu  |
|**JavaScript**|DISPONIBLE          |Aperçu  |
|**F#**        |DISPONIBLE          |         |
|**Java**      |            |Aperçu  |
|**Python**    |Expérimental|         |
|**PHP**       |Expérimental|         |
|**TypeScript**|Expérimental|         |
|**Batch**     |Expérimental|         |
|**Anniversaire**      |Expérimental|         |
|**PowerShell**|Expérimental|         |

Pour plus d’informations, consultez [langues prises en charge](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plans App service

Les fonctions sont associées à un *plan App service*. Le plan définit les ressources utilisées par l’application functions. Vous pouvez affecter des plans à une région, déterminer la taille et le nombre d’ordinateurs virtuels qui seront utilisés, et choisir un niveau tarifaire. Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan de **consommation** . Le plan de consommation met automatiquement à l’échelle le back end en fonction de la charge.

Pour plus d’informations, consultez [plans App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Créer votre première fonction

Il existe trois méthodes courantes pour créer des applications de fonction.

- Fonctions de script dans le portail.
- Créez les ressources nécessaires à l’aide de l’Azure CLI.
- Créez des fonctions localement à l’aide de votre IDE favori et publiez-les sur Azure.

Pour plus d’informations sur la création d’une fonction de script dans le portail, consultez [créer votre première fonction dans la portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Pour générer à partir de la Azure CLI, consultez [créer votre première fonction à l’aide de l’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Pour créer une fonction à partir de Visual Studio, consultez [créer votre première fonction à l’aide de Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Comprendre les déclencheurs et les liaisons

Les fonctions sont appelées par un *déclencheur* et ne peuvent en avoir qu’une seule. Outre l’appel de la fonction, certains déclencheurs servent également de liaisons. Vous pouvez également définir plusieurs liaisons en plus du déclencheur. Les *liaisons* offrent un moyen déclaratif de connecter des données à votre code. Ils peuvent être transmis (entrée) ou recevoir des données (sortie). Les déclencheurs et les liaisons rendent les fonctions faciles à utiliser. Les liaisons suppriment la surcharge liée à la création manuelle de connexions de base de données ou de système de fichiers. Toutes les informations nécessaires pour les liaisons sont contenues dans un fichier *functions. JSON* spécial pour les scripts ou déclarés avec des attributs dans le code.

Parmi les déclencheurs les plus courants, citons :

- Stockage d’objets BLOB : appelez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.
- HTTP : appelez votre fonction comme une API REST.
- Queue : appelez votre fonction lorsque des éléments existent dans une file d’attente.
- Timer : appelez votre fonction sur une cadence régulière.

Voici quelques exemples de liaisons :

- CosmosDB : Connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.
- Stockage table : travaillez avec le stockage clé/valeur à partir de votre application de fonction.
- Stockage file d’attente : récupérer facilement des éléments d’une file d’attente ou placer de nouveaux éléments dans la file d’attente.

L’exemple de fichier *functions. JSON* suivant définit un déclencheur et une liaison :

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

Dans cet exemple, la fonction est déclenchée par une modification du stockage d’objets BLOB dans le conteneur `images`. Les informations relatives au fichier étant transmises, le déclencheur joue également le rôle de liaison. Il existe une autre liaison pour placer des informations dans une file d’attente nommée `images`.

Voici le C# script de la fonction :

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé dans le stockage d’objets BLOB, et la place dans une file d’attente pour un traitement ultérieur.

Pour obtenir la liste complète des déclencheurs et des liaisons, consultez [Azure Functions les concepts de déclencheurs et de liaisons](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Serveurs proxy

Les proxies fournissent des fonctionnalités de redirection pour votre application. Les proxies exposent un point de terminaison et mappent ce point de terminaison à une autre ressource. Avec les proxies, vous pouvez :

- Rediriger une demande entrante vers un autre point de terminaison.
- Modifiez la requête entrante avant de la transmettre.
- Modifiez ou fournissez une réponse.

Les proxies sont utilisés dans des scénarios tels que :

- Simplification, raccourcissement ou modification de l’URL.
- Fournir un préfixe d’API cohérent à plusieurs services principaux.
- Simulation d’une réponse à un point de terminaison en cours de développement.
- Fournir une réponse statique à un point de terminaison connu.
- Maintien de la cohérence d’un point de terminaison d’API pendant le déplacement ou la migration du back end.

Les proxies sont stockés sous forme de définitions JSON. Voici un exemple :

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

Le proxy `Domain Redirect` prend un itinéraire abrégé et le mappe à la ressource de fonction plus longue. La transformation ressemble à ceci :

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Le proxy `Root` prend tout ce qui est envoyé à l’URL racine (`https://--shorturl--/`) et le redirige vers le site de documentation.

Un exemple d’utilisation de proxys est présenté dans la vidéo [Azure : mettez votre application dans le Cloud avec des Azure Functions sans serveur](https://channel9.msdn.com/events/Connect/2017/E102). En temps réel, une application ASP.NET Core s’exécutant sur SQL Server local est migrée vers le Cloud Azure. Les proxies sont utilisés pour aider à refactoriser un projet d’API Web traditionnel afin d’utiliser des fonctions.

Pour plus d’informations sur les proxies, consultez [utiliser Azure Functions proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Précédent](azure-serverless-platform.md)
>[Suivant](application-insights.md)
