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
# <a name="metadata"></a><span data-ttu-id="f1b06-103">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="f1b06-103">Metadata</span></span>

<span data-ttu-id="f1b06-104">Les *métadonnées* font référence à des données supplémentaires qui peuvent être utiles pendant le traitement des demandes et des réponses, mais qui ne font pas partie des données d’application réelles.</span><span class="sxs-lookup"><span data-stu-id="f1b06-104">*Metadata* refers to additional data that might be useful during the processing of requests and responses but that’s not part of the actual application data.</span></span> <span data-ttu-id="f1b06-105">Les métadonnées peuvent inclure des jetons d’authentification, des identificateurs de demande et des balises à des fins d’analyse, ainsi que des informations sur les données, comme le nombre d’enregistrements dans un DataSet.</span><span class="sxs-lookup"><span data-stu-id="f1b06-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, and information about the data, like the number of records in a dataset.</span></span>

<span data-ttu-id="f1b06-106">Il est possible d’ajouter des en-têtes de clé/valeur génériques aux messages Windows Communication Foundation (WCF) à l’aide d’un <xref:System.ServiceModel.OperationContextScope> et de la propriété <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> et de les gérer à l’aide de <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="f1b06-106">It's possible to add generic key/value headers to Windows Communication Foundation (WCF) messages by using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property and handle them by using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="f1b06-107">les appels et les réponses gRPC peuvent également inclure des métadonnées similaires aux en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1b06-107">gRPC calls and responses can also include metadata that's similar to HTTP headers.</span></span> <span data-ttu-id="f1b06-108">Ces métadonnées sont généralement invisibles pour gRPC elle-même et sont transmises pour être traitées par votre code d’application ou votre intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="f1b06-108">This metadata is mostly invisible to gRPC itself and is passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="f1b06-109">Les métadonnées sont représentées sous forme de paires clé/valeur, où la clé est une chaîne et la valeur est une chaîne ou des données binaires.</span><span class="sxs-lookup"><span data-stu-id="f1b06-109">Metadata is represented as key/value pairs, where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="f1b06-110">Vous n’avez pas besoin de spécifier des métadonnées dans le fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="f1b06-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="f1b06-111">Les métadonnées sont gérées par la classe `Metadata` du package NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) .</span><span class="sxs-lookup"><span data-stu-id="f1b06-111">Metadata is handled by the `Metadata` class of the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="f1b06-112">Cette classe peut être utilisée avec la syntaxe de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="f1b06-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="f1b06-113">Cet exemple montre comment ajouter des métadonnées à un appel à C# partir d’un client :</span><span class="sxs-lookup"><span data-stu-id="f1b06-113">This example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="f1b06-114">les services gRPC peuvent accéder aux métadonnées à partir de la propriété `RequestHeaders` de l’argument `ServerCallContext` :</span><span class="sxs-lookup"><span data-stu-id="f1b06-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="f1b06-115">Les services peuvent envoyer des métadonnées aux clients à l’aide de la propriété `ResponseTrailers` de `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="f1b06-115">Services can send metadata to clients by using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="f1b06-116">[Précédent](rpc-types.md)
>[Suivant](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="f1b06-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
