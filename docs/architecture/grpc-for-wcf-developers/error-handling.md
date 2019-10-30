---
title: Gestion des erreurs-gRPC pour les développeurs WCF
description: À ÉCRIRE
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 91f5789d8ed0f01f3ce2f3f9a6c6ccf14f245290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094230"
---
# <a name="error-handling"></a><span data-ttu-id="9c459-103">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="9c459-103">Error handling</span></span>

<span data-ttu-id="9c459-104">WCF utilise `FaultException<T>` et `FaultContract` pour fournir des informations d’erreur détaillées, notamment la prise en charge de la norme SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="9c459-104">WCF uses `FaultException<T>` and `FaultContract` to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="9c459-105">Malheureusement, la version actuelle de gRPC ne dispose pas de la sophistication trouvée avec WCF et ne dispose que d’une gestion des erreurs intégrée limitée basée sur des codes d’État et des métadonnées simples.</span><span class="sxs-lookup"><span data-stu-id="9c459-105">Unfortunately, the current version of gRPC lacks the sophistication found with WCF and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="9c459-106">Le tableau suivant est un guide rapide sur les codes d’état les plus couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="9c459-106">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="9c459-107">Code d’état</span><span class="sxs-lookup"><span data-stu-id="9c459-107">Status Code</span></span> | <span data-ttu-id="9c459-108">Problème</span><span class="sxs-lookup"><span data-stu-id="9c459-108">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="9c459-109">La méthode n’a pas été écrite.</span><span class="sxs-lookup"><span data-stu-id="9c459-109">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="9c459-110">Problème avec l’ensemble du service.</span><span class="sxs-lookup"><span data-stu-id="9c459-110">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="9c459-111">Réponse non valide.</span><span class="sxs-lookup"><span data-stu-id="9c459-111">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="9c459-112">Problème d’encodage/décodage.</span><span class="sxs-lookup"><span data-stu-id="9c459-112">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="9c459-113">Échec de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="9c459-113">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="9c459-114">Échec de l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="9c459-114">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="9c459-115">L’appel a été annulé, généralement par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="9c459-115">Call was canceled, usually by the caller.</span></span> |

## <a name="raising-errors-in-aspnet-core-grpc"></a><span data-ttu-id="9c459-116">Déclenchement d’erreurs dans ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="9c459-116">Raising errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="9c459-117">Un service ASP.NET Core gRPC peut envoyer une réponse d’erreur en levant une `RpcException`, qui peut être interceptée par le client comme si elle était dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="9c459-117">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="9c459-118">Le `RpcException` doit inclure un code d’État et une description, et peut éventuellement inclure des métadonnées et un message d’exception plus long.</span><span class="sxs-lookup"><span data-stu-id="9c459-118">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="9c459-119">Les métadonnées peuvent être utilisées pour envoyer des données de prise en charge, de la même façon que `FaultContract` objets peuvent contenir des données supplémentaires pour les erreurs WCF.</span><span class="sxs-lookup"><span data-stu-id="9c459-119">The metadata can be used to send supporting data, similar to how `FaultContract` objects could carry additional data for WCF errors.</span></span>

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

## <a name="catching-errors-in-grpc-clients"></a><span data-ttu-id="9c459-120">Interception des erreurs dans les clients gRPC</span><span class="sxs-lookup"><span data-stu-id="9c459-120">Catching errors in gRPC clients</span></span>

<span data-ttu-id="9c459-121">Tout comme les clients WCF peuvent intercepter les erreurs de <xref:System.ServiceModel.FaultException%601>, un client gRPC peut intercepter une `RpcException` pour gérer les erreurs.</span><span class="sxs-lookup"><span data-stu-id="9c459-121">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="9c459-122">Étant donné que `RpcException` n’est pas un type générique, vous ne pouvez pas intercepter différents types d’erreur C#dans différents blocs, mais vous pouvez utiliser la fonctionnalité des *filtres d’exception* de pour déclarer des blocs`catch`distincts pour différents codes d’État, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9c459-122">Since `RpcException` isn't a generic type, you can't catch different error types in different blocks, but you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="9c459-123">Lorsque vous fournissez des métadonnées supplémentaires pour les erreurs, veillez à documenter les clés et les valeurs pertinentes dans la documentation de votre API ou dans les commentaires de votre fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="9c459-123">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="9c459-124">Modèle d’erreur plus riche gRPC</span><span class="sxs-lookup"><span data-stu-id="9c459-124">gRPC Richer Error Model</span></span>

<span data-ttu-id="9c459-125">À l’avenir, Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui est plus semblable à C# WCF [FaultContract](xref:System.ServiceModel.FaultContractAttribute), mais n’est pas encore pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9c459-125">Looking ahead, Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that is more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but isn't supported in C# yet.</span></span> <span data-ttu-id="9c459-126">Actuellement, il n’est disponible que pour Go, Java, Python C++et, mais la C# prise en charge de est attendue l’année prochaine.</span><span class="sxs-lookup"><span data-stu-id="9c459-126">Currently, it's only available for Go, Java, Python and C++, but support for C# is expected to come next year.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9c459-127">[Précédent](metadata.md)
>[Suivant](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="9c459-127">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
