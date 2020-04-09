---
title: Gestion d’erreurs - gRPC pour WCF Developers
description: Sujets relatifs à la gestion des erreurs dans gRPC. Comprend un tableau des codes de statut les plus couramment utilisés.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988945"
---
# <a name="error-handling"></a><span data-ttu-id="6f378-104">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="6f378-104">Error handling</span></span>

<span data-ttu-id="6f378-105">Windows Communication Foundation (WCF) utilise <xref:System.ServiceModel.FaultException%601> et [FaultContract](xref:System.ServiceModel.FaultContractAttribute) pour fournir des informations détaillées sur les erreurs, y compris en tenant compte de la norme SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="6f378-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="6f378-106">Malheureusement, la version actuelle de gRPC n’a pas la sophistication trouvée avec WCF, et n’a qu’une manipulation limitée d’erreurs intégrées basée sur des codes de statut simples et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6f378-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="6f378-107">Le tableau suivant est un guide rapide des codes d’état les plus couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="6f378-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="6f378-108">Code d’état</span><span class="sxs-lookup"><span data-stu-id="6f378-108">Status code</span></span> | <span data-ttu-id="6f378-109">Problème</span><span class="sxs-lookup"><span data-stu-id="6f378-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="6f378-110">La méthode n’a pas été écrite.</span><span class="sxs-lookup"><span data-stu-id="6f378-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="6f378-111">Problème avec l’ensemble du service.</span><span class="sxs-lookup"><span data-stu-id="6f378-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="6f378-112">Réponse invalide.</span><span class="sxs-lookup"><span data-stu-id="6f378-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="6f378-113">Problème avec l’encodage/décodage.</span><span class="sxs-lookup"><span data-stu-id="6f378-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="6f378-114">Échec de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="6f378-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="6f378-115">Échec de l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="6f378-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="6f378-116">L’appel a été annulé, habituellement par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6f378-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="6f378-117">Augmenter les erreurs dans ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="6f378-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="6f378-118">Un ASP.NET service Core gRPC peut envoyer une `RpcException`réponse d’erreur en jetant un , qui peut être pris par le client comme si elle était dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="6f378-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="6f378-119">Le `RpcException` doit inclure un code de statut et une description, et peut inclure optionnellement des métadonnées et un message d’exception plus long.</span><span class="sxs-lookup"><span data-stu-id="6f378-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="6f378-120">Les métadonnées peuvent être utilisées pour `FaultContract` envoyer des données à l’appui, similaires à la façon dont les objets peuvent transporter des données supplémentaires pour les erreurs WCF.</span><span class="sxs-lookup"><span data-stu-id="6f378-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="6f378-121">Attraper les erreurs chez les clients gRPC</span><span class="sxs-lookup"><span data-stu-id="6f378-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="6f378-122">Tout comme les clients <xref:System.ServiceModel.FaultException%601> WCF peuvent attraper des `RpcException` erreurs, un client gRPC peut attraper un pour gérer les erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f378-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="6f378-123">Parce `RpcException` que n’est pas un type générique, vous ne pouvez pas attraper différents types d’erreurs dans différents blocs.</span><span class="sxs-lookup"><span data-stu-id="6f378-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="6f378-124">Mais vous pouvez utiliser la fonction de *filtres d’exception* de C pour déclarer des blocs distincts `catch` pour différents codes de statut, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6f378-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="6f378-125">Lorsque vous fournissez des métadonnées supplémentaires pour les erreurs, assurez-vous de documenter les clés et les valeurs pertinentes dans votre documentation API, ou dans les commentaires dans votre `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="6f378-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="6f378-126">gRPC modèle d’erreur plus riche</span><span class="sxs-lookup"><span data-stu-id="6f378-126">gRPC richer error model</span></span>

<span data-ttu-id="6f378-127">Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui ressemble plus à [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF , mais ce modèle n’est pas pris en charge dans C 'encore.</span><span class="sxs-lookup"><span data-stu-id="6f378-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="6f378-128">Actuellement, il n’est disponible que pour Go, Java, Python et C.</span><span class="sxs-lookup"><span data-stu-id="6f378-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6f378-129">[Suivant précédent](metadata.md)
>[Next](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="6f378-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
