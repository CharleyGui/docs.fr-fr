---
title: Fonctions Azure - Applications sans serveur
description: Les fonctions Azure fournissent des capacités sans serveur sur plusieurs langues (C, JavaScript, Java) et des plates-formes pour fournir un code instantané axé sur les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401612"
---
# <a name="azure-functions"></a>Azure Functions

Les fonctions Azure offrent une expérience de calcul sans serveur. Une fonction est invoquée par un *déclencheur* (comme l’accès à un point de terminaison HTTP ou à une minuterie) et exécute un bloc de code ou de logique métier. Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources comme le stockage et les files d’attente.

![Logo azure fonctions](./media/azure-functions-logo.png)

Il existe deux versions du cadre Azure Functions. La version héritée prend en charge le cadre .NET complet et le nouveau runtime prend en charge les applications cross-platform .NET Core. D’autres langues en dehors de C’telles que JavaScript, F' et Java sont prises en charge. Les fonctions créées dans le portail fournissent une syntaxe scriptive riche. Les fonctions créées en tant que projets autonomes peuvent être déployées avec un soutien et des capacités de plate-forme complets.

Pour plus d’informations, voir [la documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Fonctions v1 vs v2

Il existe deux versions de l’heure d’exécution Azure Functions : 1.x et 2.x. La version 1.x est généralement disponible (GA). Il prend en charge le développement .NET à partir du portail ou des machines Windows et utilise le cadre .NET. 1.x prend en charge C, JavaScript et F, avec un support expérimental pour Python, PHP, TypeScript, Batch, Bash et PowerShell.

[Version 2.x est également généralement disponible dès maintenant](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Il tire parti de .NET Core et prend en charge le développement multiplateforme sur les machines Windows, macOS et Linux. 2.x ajoute un support de première classe pour Java, mais ne prend pas encore directement en charge l’une des langues expérimentales. La version 2.x utilise un nouveau modèle d’extéabilité contraignante qui permet des extensions tierces à la plate-forme, une version indépendante des fixations et un environnement d’exécution plus rationalisé.

> **Il ya un problème connu dans 1.x avec [le soutien réorienté contraignant](https://github.com/Azure/azure-functions-host/issues/992).** La question est spécifique au développement .NET. Les projets ayant des dépendances sur les bibliothèques qui sont une version différente des bibliothèques incluses dans le temps d’exécution sont touchés. L’équipe des fonctions s’est engagée à faire des progrès concrets sur le problème. L’équipe abordera les redirections de liaison en 2.x avant qu’elle n’entre dans la disponibilité générale. La déclaration officielle de l’équipe avec des correctifs suggérés et des solutions de contournement est disponible ici: [résolution de l’Assemblée dans azure Fonctions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Pour plus d’informations, voir [Comparez 1.x et 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Soutien linguistique de programmation

Les langues suivantes sont prises en charge soit en disponibilité générale (GA), en avant-première, soit expérimentale.

|Langage      |1.x         |2.x      |
|--------------|------------|---------|
|**C #**        |GA          |PRÉVERSION  |
|**Javascript**|GA          |PRÉVERSION  |
|**F #**        |GA          |         |
|**Java**      |            |PRÉVERSION  |
|**Python**    |Expérimental|         |
|**Php**       |Expérimental|         |
|**TypeScript**|Expérimental|         |
|**Lot**     |Expérimental|         |
|**Bash**      |Expérimental|         |
|**PowerShell**|Expérimental|         |

Pour en savoir plus, consultez [Langages pris en charge](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plans de service App

Les fonctions sont soutenues par un *plan de service d’application*. Le plan définit les ressources utilisées par l’application fonctions. Vous pouvez affecter des plans à une région, déterminer la taille et le nombre de machines virtuelles qui seront utilisées, et choisir un niveau de tarification. Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan **de consommation.** Le plan de consommation permettra d’échelle de l’arrière automatiquement en fonction de la charge.

Pour plus d’informations, consultez [les plans de service App](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Créer votre première fonction

Il existe trois façons courantes de créer des applications de fonction.

- Fonctions de script dans le portail.
- Créez les ressources nécessaires à l’aide du CLI Azure.
- Construisez des fonctions localement à l’aide de votre IDE préféré et publiez-les sur Azure.

Pour plus d’informations sur la création d’une fonction scénarisée dans le portail, voir [Créer votre première fonction dans le portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Pour construire à partir du CLI Azure, voir [Créer votre première fonction à l’aide de l’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Pour créer une fonction à partir de Visual Studio, voir [Créer votre première fonction en utilisant Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Comprendre les déclencheurs et les fixations

Les fonctions sont invoquées par un *déclencheur* et peuvent en avoir exactement une. En plus d’invoquer la fonction, certains déclencheurs servent également de fixations. Vous pouvez également définir plusieurs liaisons en plus de la gâchette. *Les liaisons* fournissent un moyen déclaratif de connecter les données à votre code. Ils peuvent être transmis (entrée) ou recevoir des données (sortie). Les déclencheurs et les fixations facilitent le travail des fonctions. Les liaisons suppriment les frais généraux de la création manuelle de bases de données ou de connexions système de fichiers. Toutes les informations nécessaires pour les liaisons sont contenues dans un fichier *functions.json* spécial pour les scripts ou déclaré avec des attributs dans le code.

Voici quelques déclencheurs courants :

- Stockage Blob : invoquez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.
- HTTP : invoquez votre fonction comme une API REST.
- File d’attente : invoquez votre fonction lorsque des éléments existent dans une file d’attente.
- Minuterie : invoquez votre fonction sur une cadence régulière.

Voici quelques exemples de liaisons :

- CosmosDB : connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.
- Stockage de table : travaillez avec le stockage de clé/valeur à partir de votre application de fonction.
- Stockage de file d’attente : récupérez facilement des articles d’une file d’attente ou placez de nouveaux éléments dans la file d’attente.

L’exemple suivant *functions.json* fichier définit un déclencheur et une liaison:

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

Dans cet exemple, la fonction est déclenchée par `images` un changement de stockage blob dans le conteneur. Les informations pour le fichier sont transmises, de sorte que le déclencheur agit également comme une liaison. Une autre liaison existe pour mettre `images`l’information sur une file d’attente nommée .

Voici le script C pour la fonction:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé sur le stockage blob, et le place sur une file d’attente pour le traitement ultérieur.

Pour une liste complète des déclencheurs et des fixations, voir [les déclencheurs et les concepts de fixations Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxies

Les procurations fournissent des fonctionnalités de redirection pour votre application. Les procurations exposent un point de terminaison et cartographient ce point de terminaison vers une autre ressource. Avec des procurations, vous pouvez :

- Réorienter une demande entrante à un autre critère d’évaluation.
- Modifier la demande entrante avant qu’elle ne soit transmise.
- Modifier ou fournir une réponse.

Les procurations sont utilisées pour des scénarios tels que :

- Simplifier, raccourcir ou modifier l’URL.
- Fournir un préfixe API cohérent à plusieurs services back-end.
- Se moquer d’une réponse à un point de terminaison en cours d’élaboration.
- Fournir une réponse statique à un critère d’évaluation bien connu.
- Maintenir un point de terminaison API cohérent pendant que l’extrémité arrière est déplacée ou migrée.

Les procurations sont stockées sous forme de définitions JSON. Voici un exemple :

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

Le `Domain Redirect` proxy prend un itinéraire raccourci et le cartographie à la ressource de fonction plus longue. La transformation ressemble à:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Le `Root` proxy prend tout ce`https://--shorturl--/`qui est envoyé à l’URL racine ( ) et la redirige vers le site de documentation.

Un exemple d’utilisation de procurations est montré dans la vidéo [Azure: Apportez votre application au cloud avec des fonctions Azure sans serveur](https://channel9.msdn.com/events/Connect/2017/E102). En temps réel, une application ASP.NET Core fonctionnant sur SQL Server local est migrée vers le Cloud Azure. Les procurations sont utilisées pour aider à refactorer un projet traditionnel d’API Web pour utiliser des fonctions.

Pour plus d’informations sur Proxies, voir [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Suivant précédent](azure-serverless-platform.md)
>[Next](application-insights.md)
