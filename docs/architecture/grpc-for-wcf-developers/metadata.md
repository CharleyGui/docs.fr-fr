---
title: Metadata-gRPC pour les développeurs WCF
description: Comment les métadonnées sont utilisées dans gRPC pour passer un contexte supplémentaire entre les clients et les serveurs.
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628577"
---
# <a name="metadata"></a>Métadonnées

Les *métadonnées* font référence à des données supplémentaires qui peuvent être utiles pendant le traitement des demandes et des réponses, mais qui ne font pas partie des données d’application réelles. Les métadonnées peuvent inclure des jetons d’authentification, des identificateurs de demande et des balises à des fins d’analyse, ainsi que des informations sur les données, comme le nombre d’enregistrements dans un DataSet.

Il est possible d’ajouter des en-têtes de clé/valeur génériques aux messages Windows Communication Foundation (WCF) à l’aide d’un <xref:System.ServiceModel.OperationContextScope> et de la propriété <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> et de les gérer à l’aide de <xref:System.ServiceModel.Channels.MessageProperties>.

les appels et les réponses gRPC peuvent également inclure des métadonnées similaires aux en-têtes HTTP. Ces métadonnées sont généralement invisibles pour gRPC elle-même et sont transmises pour être traitées par votre code d’application ou votre intergiciel (middleware). Les métadonnées sont représentées sous forme de paires clé/valeur, où la clé est une chaîne et la valeur est une chaîne ou des données binaires. Vous n’avez pas besoin de spécifier des métadonnées dans le fichier `.proto`.

Les métadonnées sont gérées par la classe `Metadata` du package NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Cette classe peut être utilisée avec la syntaxe de l’initialiseur de collection.

Cet exemple montre comment ajouter des métadonnées à un appel à C# partir d’un client :

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

Les services peuvent envoyer des métadonnées aux clients à l’aide de la propriété `ResponseTrailers` de `ServerCallContext`:

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
