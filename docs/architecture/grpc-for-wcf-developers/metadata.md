---
title: Metadata-gRPC pour les développeurs WCF
description: Utilisation des métadonnées dans gRPC pour passer un contexte supplémentaire entre les clients et les serveurs
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 32559b3404b12f366fc1624299d04cff9faad9d6
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846617"
---
# <a name="metadata"></a>Métadonnées

Les « métadonnées » font référence à des données supplémentaires qui peuvent être utiles lors du traitement des demandes et des réponses, mais qui ne font pas partie des données d’application réelles. Les métadonnées peuvent inclure des jetons d’authentification, des identificateurs de demande et des balises à des fins d’analyse, ou des informations sur les données telles que le nombre d’enregistrements dans un DataSet.

Il est possible d’ajouter des en-têtes de clé/valeur génériques aux messages WCF à l’aide d’un <xref:System.ServiceModel.OperationContextScope> et de la propriété <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType>, et de les gérer à l’aide de <xref:System.ServiceModel.Channels.MessageProperties>.

les appels et les réponses gRPC peuvent également inclure des métadonnées similaires aux en-têtes HTTP. Celles-ci sont pratiquement invisibles pour gRPC elle-même et sont transmises pour être traitées par votre code d’application ou votre intergiciel (middleware). Les métadonnées sont représentées sous forme de paires clé/valeur où la clé est une chaîne et la valeur est une chaîne ou des données binaires. Vous n’avez pas besoin de spécifier des métadonnées dans le fichier `.proto`.

Les métadonnées sont gérées à l’aide de la classe `Metadata` à partir du package NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Cette classe peut être utilisée avec la syntaxe de l’initialiseur de collection.

L’exemple suivant montre comment ajouter des métadonnées à un appel à C# partir d’un client :

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

les services gRPC peuvent accéder aux métadonnées à partir de la propriété `RequestHeaders` de l’argument `ServerCallContext` :

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

Les services peuvent envoyer des métadonnées aux clients à l’aide de la propriété `ResponseTrailers` de `ServerCallContext` :

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Précédent](rpc-types.md)
>[Suivant](error-handling.md)
