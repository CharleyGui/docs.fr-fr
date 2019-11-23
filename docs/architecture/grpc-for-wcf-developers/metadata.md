---
title: Metadata-gRPC pour les développeurs WCF
description: Utilisation des métadonnées dans gRPC pour passer un contexte supplémentaire entre les clients et les serveurs
ms.date: 09/02/2019
ms.openlocfilehash: 723d877bfbf0c2b0785949ff15939aedbac4d4e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971979"
---
# <a name="metadata"></a><span data-ttu-id="4a9b5-103">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="4a9b5-103">Metadata</span></span>

<span data-ttu-id="4a9b5-104">Les « métadonnées » font référence à des données supplémentaires qui peuvent être utiles lors du traitement des demandes et des réponses, mais qui ne font pas partie des données d’application réelles.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="4a9b5-105">Les métadonnées peuvent inclure des jetons d’authentification, des identificateurs de demande et des balises à des fins d’analyse, ou des informations sur les données telles que le nombre d’enregistrements dans un DataSet.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="4a9b5-106">Il est possible d’ajouter des en-têtes de clé/valeur génériques aux messages WCF à l’aide d’un <xref:System.ServiceModel.OperationContextScope> et de la propriété <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType>, et de les gérer à l’aide de <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="4a9b5-107">les appels et les réponses gRPC peuvent également inclure des métadonnées similaires aux en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="4a9b5-108">Celles-ci sont pratiquement invisibles pour gRPC elle-même et sont transmises pour être traitées par votre code d’application ou votre intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="4a9b5-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="4a9b5-109">Les métadonnées sont représentées sous forme de paires clé/valeur où la clé est une chaîne et la valeur est une chaîne ou des données binaires.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="4a9b5-110">Vous n’avez pas besoin de spécifier des métadonnées dans le fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="4a9b5-111">Les métadonnées sont gérées à l’aide de la classe `Metadata` à partir du package NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) .</span><span class="sxs-lookup"><span data-stu-id="4a9b5-111">Metadata is handled using the `Metadata` class from the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="4a9b5-112">Cette classe peut être utilisée avec la syntaxe de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="4a9b5-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="4a9b5-113">L’exemple suivant montre comment ajouter des métadonnées à un appel à C# partir d’un client :</span><span class="sxs-lookup"><span data-stu-id="4a9b5-113">The following example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="4a9b5-114">les services gRPC peuvent accéder aux métadonnées à partir de la propriété `RequestHeaders` de l’argument `ServerCallContext` :</span><span class="sxs-lookup"><span data-stu-id="4a9b5-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="4a9b5-115">Les services peuvent envoyer des métadonnées aux clients à l’aide de la propriété `ResponseTrailers` de `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="4a9b5-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="4a9b5-116">[Précédent](rpc-types.md)
>[Suivant](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="4a9b5-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
