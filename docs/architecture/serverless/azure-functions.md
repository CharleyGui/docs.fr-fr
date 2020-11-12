---
title: Applications sans serveur Azure Functions
description: Azure Functions offre des fonctionnalités sans serveur dans plusieurs langues (C#, JavaScript, Java) et des plateformes pour fournir un code de mise à l’échelle instantanée piloté par les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 08e1aaecdee753dc25cca0d6356caaafae1ad510
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557114"
---
# <a name="azure-functions"></a>Azure Functions

Azure Functions fournir une expérience de calcul sans serveur. Une fonction est appelée par un *déclencheur* (comme l’accès à un point de terminaison http ou une minuterie) et exécute un bloc de code ou une logique métier. Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources telles que le stockage et les files d’attente.

![Logo Azure Functions](./media/azure-functions-logo.png)

La version de Runtime actuelle 3,0 prend en charge les applications .NET Core 3,1 multiplateforme. Des langages supplémentaires en plus de C#, tels que JavaScript, F # et Java, sont pris en charge. Les fonctions créées dans le portail fournissent une syntaxe de script riche. Les fonctions créées en tant que projets autonomes peuvent être déployées avec une prise en charge complète des plateformes et des fonctionnalités.

Pour plus d’informations, consultez [la documentation Azure Functions](/azure/azure-functions).

## <a name="programming-language-support"></a>Prise en charge des langages de programmation

Les langues suivantes sont toutes prises en charge dans la disponibilité générale (GA).

|Langage      |Runtimes pris en charge|
|--------------|------------------|
|**C#**        |.NET Core 3.1     |
|**JavaScript**|Nœud 10 & 12      |
|**F#**        |.NET Core 3.1     |
|**Java**      |Java 8            |
|**Python**    |Python 3,6, 3,7, & 3,8|
|**TypeScript**|Nœud 10 & 12 (via JavaScript)|
|**PowerShell**|PowerShell Core 6|

Pour en savoir plus, consultez [Langages pris en charge](/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plans App service

Les fonctions sont associées à un *plan App service*. Le plan définit les ressources utilisées par l’application functions. Vous pouvez affecter des plans à une région, déterminer la taille et le nombre d’ordinateurs virtuels qui seront utilisés, et choisir un niveau tarifaire. Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan de **consommation** . Le plan de consommation met automatiquement à l’échelle le back end en fonction de la charge.

Le [plan Premium](/azure/azure-functions/functions-premium-plan)est une autre option d’hébergement pour les applications de fonction. Ce plan fournit une instance « Always on » pour éviter le démarrage à froid, prend en charge des fonctionnalités avancées telles que la connectivité de réseau virtuel et s’exécute sur du matériel Premium.

Pour plus d’informations, consultez [plans App service](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Créer votre première fonction

Il existe trois méthodes courantes pour créer des applications de fonction.

- Fonctions de script dans le portail.
- Créez les ressources nécessaires à l’aide de l’Azure CLI.
- Créez des fonctions localement à l’aide de votre IDE favori et publiez-les sur Azure.

Pour plus d’informations sur la création d’une fonction de script dans le portail, consultez [créer votre première fonction dans la portail Azure](/azure/azure-functions/functions-create-first-azure-function).

Pour générer à partir de la Azure CLI, consultez [créer votre première fonction à l’aide de l’Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Pour créer une fonction à partir de Visual Studio, consultez [créer votre première fonction à l’aide de Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Comprendre les déclencheurs et les liaisons

Les fonctions sont appelées par un *déclencheur* et ne peuvent en avoir qu’une seule. Outre l’appel de la fonction, certains déclencheurs servent également de liaisons. Vous pouvez également définir plusieurs liaisons en plus du déclencheur. Les *liaisons* offrent un moyen déclaratif de connecter des données à votre code. Ils peuvent être transmis (entrée) ou recevoir des données (sortie). Les déclencheurs et les liaisons rendent les fonctions faciles à utiliser. Les liaisons suppriment la surcharge liée à la création manuelle de connexions de base de données ou de système de fichiers. Toutes les informations nécessaires pour les liaisons sont contenues dans unfunctions.jsspécial *sur* le fichier pour les scripts ou déclarés avec des attributs dans le code.

Parmi les déclencheurs les plus courants, citons :

- Stockage d’objets BLOB : appelez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.
- HTTP : appelez votre fonction comme une API REST.
- Queue : appelez votre fonction lorsque des éléments existent dans une file d’attente.
- Timer : appelez votre fonction sur une cadence régulière.

Voici quelques exemples de liaisons :

- CosmosDB : Connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.
- Stockage table : travaillez avec le stockage clé/valeur à partir de votre application de fonction.
- Stockage file d’attente : récupérer facilement des éléments d’une file d’attente ou placer de nouveaux éléments dans la file d’attente.

L’exemple suivant *functions.jssur* le fichier définit un déclencheur et une liaison :

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

Dans cet exemple, la fonction est déclenchée par une modification du stockage d’objets BLOB dans le `images` conteneur. Les informations relatives au fichier étant transmises, le déclencheur joue également le rôle de liaison. Il existe une autre liaison pour placer des informations dans une file d’attente nommée `images` .

Voici le script C# pour la fonction :

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé dans le stockage d’objets BLOB, et la place dans une file d’attente pour un traitement ultérieur.

Pour obtenir la liste complète des déclencheurs et des liaisons, consultez [Azure Functions les concepts de déclencheurs et de liaisons](/azure/azure-functions/functions-triggers-bindings).

>[!div class="step-by-step"]
>[Précédent](azure-serverless-platform.md) 
> [Suivant](application-insights.md)
