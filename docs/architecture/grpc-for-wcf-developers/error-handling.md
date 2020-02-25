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
# <a name="error-handling"></a>Gestion des erreurs

Windows Communication Foundation (WCF) utilise <xref:System.ServiceModel.FaultException%601> et [FaultContract](xref:System.ServiceModel.FaultContractAttribute) pour fournir des informations détaillées sur l’erreur, notamment la prise en charge de la norme SOAP Fault.

Malheureusement, la version actuelle de gRPC ne dispose pas de la sophistication trouvée avec WCF et ne dispose que d’une gestion des erreurs intégrée limitée basée sur des codes d’État et des métadonnées simples. Le tableau suivant est un guide rapide sur les codes d’état les plus couramment utilisés :

| Code d’état | Problème |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | La méthode n’a pas été écrite. |
| `GRPC_STATUS_UNAVAILABLE` | Problème avec l’ensemble du service. |
| `GRPC_STATUS_UNKNOWN` | Réponse non valide. |
| `GRPC_STATUS_INTERNAL` | Problème d’encodage/décodage. |
| `GRPC_STATUS_UNAUTHENTICATED` | Échec de l'authentification. |
| `GRPC_STATUS_PERMISSION_DENIED` | Échec de l’autorisation. |
| `GRPC_STATUS_CANCELLED` | L’appel a été annulé, généralement par l’appelant. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Déclencher des erreurs dans ASP.NET Core gRPC

Un service ASP.NET Core gRPC peut envoyer une réponse d’erreur en levant une `RpcException`, qui peut être interceptée par le client comme si elle était dans le même processus. Le `RpcException` doit inclure un code d’État et une description, et peut éventuellement inclure des métadonnées et un message d’exception plus long. Les métadonnées peuvent être utilisées pour envoyer des données de prise en charge, de la même façon que `FaultContract` objets peuvent contenir des données supplémentaires pour les erreurs WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Intercepter les erreurs dans les clients gRPC

Tout comme les clients WCF peuvent intercepter les erreurs de <xref:System.ServiceModel.FaultException%601>, un client gRPC peut intercepter une `RpcException` pour gérer les erreurs. Étant donné que `RpcException` n’est pas un type générique, vous ne pouvez pas intercepter différents types d’erreur dans différents blocs. Toutefois, vous pouvez C#utiliser la fonctionnalité de *filtres d’exception* de pour déclarer des blocs de `catch` distincts pour différents codes d’État, comme indiqué dans l’exemple suivant :

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
> Lorsque vous fournissez des métadonnées supplémentaires pour les erreurs, veillez à documenter les clés et les valeurs pertinentes dans la documentation de votre API ou dans les commentaires de votre fichier `.proto`.

## <a name="grpc-richer-error-model"></a>modèle d’erreur plus riche gRPC

Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui est plus semblable à C# WCF [FaultContract](xref:System.ServiceModel.FaultContractAttribute), mais ce modèle n’est pas encore pris en charge. Actuellement, il n’est disponible que pour Go, Java, Python et C++.

>[!div class="step-by-step"]
>[Précédent](metadata.md)
>[Suivant](ws-protocols.md)
