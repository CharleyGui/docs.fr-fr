---
title: Gestion des erreurs-gRPC pour les développeurs WCF
description: Rubriques relatives à la gestion des erreurs dans gRPC. Contient un tableau des codes d’état les plus couramment utilisés.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542791"
---
# <a name="error-handling"></a><span data-ttu-id="4c353-104">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="4c353-104">Error handling</span></span>

<span data-ttu-id="4c353-105">Windows Communication Foundation (WCF) utilise <xref:System.ServiceModel.FaultException%601> et [FaultContract](xref:System.ServiceModel.FaultContractAttribute) pour fournir des informations détaillées sur l’erreur, notamment la prise en charge de la norme SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="4c353-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="4c353-106">Malheureusement, la version actuelle de gRPC ne dispose pas de la sophistication trouvée avec WCF et ne dispose que d’une gestion des erreurs intégrée limitée basée sur des codes d’État et des métadonnées simples.</span><span class="sxs-lookup"><span data-stu-id="4c353-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="4c353-107">Le tableau suivant est un guide rapide sur les codes d’état les plus couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="4c353-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="4c353-108">Code d’état</span><span class="sxs-lookup"><span data-stu-id="4c353-108">Status code</span></span> | <span data-ttu-id="4c353-109">Problème</span><span class="sxs-lookup"><span data-stu-id="4c353-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="4c353-110">La méthode n’a pas été écrite.</span><span class="sxs-lookup"><span data-stu-id="4c353-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="4c353-111">Problème avec l’ensemble du service.</span><span class="sxs-lookup"><span data-stu-id="4c353-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="4c353-112">Réponse non valide.</span><span class="sxs-lookup"><span data-stu-id="4c353-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="4c353-113">Problème d’encodage/décodage.</span><span class="sxs-lookup"><span data-stu-id="4c353-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="4c353-114">Échec de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="4c353-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="4c353-115">Échec de l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="4c353-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="4c353-116">L’appel a été annulé, généralement par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="4c353-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="4c353-117">Déclencher des erreurs dans ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="4c353-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="4c353-118">Un service ASP.NET Core gRPC peut envoyer une réponse d’erreur en levant une `RpcException`, qui peut être interceptée par le client comme si elle était dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="4c353-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="4c353-119">Le `RpcException` doit inclure un code d’État et une description, et peut éventuellement inclure des métadonnées et un message d’exception plus long.</span><span class="sxs-lookup"><span data-stu-id="4c353-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="4c353-120">Les métadonnées peuvent être utilisées pour envoyer des données de prise en charge, de la même façon que `FaultContract` objets peuvent contenir des données supplémentaires pour les erreurs WCF.</span><span class="sxs-lookup"><span data-stu-id="4c353-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="4c353-121">Intercepter les erreurs dans les clients gRPC</span><span class="sxs-lookup"><span data-stu-id="4c353-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="4c353-122">Tout comme les clients WCF peuvent intercepter les erreurs de <xref:System.ServiceModel.FaultException%601>, un client gRPC peut intercepter une `RpcException` pour gérer les erreurs.</span><span class="sxs-lookup"><span data-stu-id="4c353-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="4c353-123">Étant donné que `RpcException` n’est pas un type générique, vous ne pouvez pas intercepter différents types d’erreur dans différents blocs.</span><span class="sxs-lookup"><span data-stu-id="4c353-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="4c353-124">Toutefois, vous pouvez C#utiliser la fonctionnalité de *filtres d’exception* de pour déclarer des blocs de `catch` distincts pour différents codes d’État, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4c353-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> <span data-ttu-id="4c353-125">Lorsque vous fournissez des métadonnées supplémentaires pour les erreurs, veillez à documenter les clés et les valeurs pertinentes dans la documentation de votre API ou dans les commentaires de votre fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="4c353-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="4c353-126">modèle d’erreur plus riche gRPC</span><span class="sxs-lookup"><span data-stu-id="4c353-126">gRPC richer error model</span></span>

<span data-ttu-id="4c353-127">Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui est plus semblable à C# WCF [FaultContract](xref:System.ServiceModel.FaultContractAttribute), mais ce modèle n’est pas encore pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4c353-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="4c353-128">Actuellement, il n’est disponible que pour Go, Java, Python et C++.</span><span class="sxs-lookup"><span data-stu-id="4c353-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4c353-129">[Précédent](metadata.md)
>[Suivant](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="4c353-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
