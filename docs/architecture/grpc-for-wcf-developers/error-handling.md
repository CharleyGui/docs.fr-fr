---
title: Gestion des erreurs-gRPC pour les développeurs WCF
description: À ÉCRIRE
ms.date: 09/02/2019
ms.openlocfilehash: 2c44bd9264c877a7c7a86c115b6da9f759006016
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967794"
---
# <a name="error-handling"></a>Gestion des erreurs

WCF utilise `FaultException<T>` et `FaultContract` pour fournir des informations d’erreur détaillées, notamment la prise en charge de la norme SOAP Fault.

Malheureusement, la version actuelle de gRPC ne dispose pas de la sophistication trouvée avec WCF et ne dispose que d’une gestion des erreurs intégrée limitée basée sur des codes d’État et des métadonnées simples. Le tableau suivant est un guide rapide sur les codes d’état les plus couramment utilisés :

| Code d’état | Problème |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | La méthode n’a pas été écrite. |
| `GRPC_STATUS_UNAVAILABLE` | Problème avec l’ensemble du service. |
| `GRPC_STATUS_UNKNOWN` | Réponse non valide. |
| `GRPC_STATUS_INTERNAL` | Problème d’encodage/décodage. |
| `GRPC_STATUS_UNAUTHENTICATED` | Échec de l’authentification. |
| `GRPC_STATUS_PERMISSION_DENIED` | Échec de l’autorisation. |
| `GRPC_STATUS_CANCELLED` | L’appel a été annulé, généralement par l’appelant. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>Déclenchement d’erreurs dans ASP.NET Core gRPC

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

## <a name="catching-errors-in-grpc-clients"></a>Interception des erreurs dans les clients gRPC

Tout comme les clients WCF peuvent intercepter les erreurs de <xref:System.ServiceModel.FaultException%601>, un client gRPC peut intercepter une `RpcException` pour gérer les erreurs. Étant donné que `RpcException` n’est pas un type générique, vous ne pouvez pas intercepter différents types d’erreur C#dans différents blocs, mais vous pouvez utiliser la fonctionnalité des *filtres d’exception* de pour déclarer des blocs `catch` distincts pour différents codes d’État, comme indiqué dans l’exemple suivant :

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

## <a name="grpc-richer-error-model"></a>Modèle d’erreur plus riche gRPC

À l’avenir, Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui est plus semblable à C# WCF [FaultContract](xref:System.ServiceModel.FaultContractAttribute), mais n’est pas encore pris en charge. Actuellement, il n’est disponible que pour Go, Java, Python C++et, mais la C# prise en charge de est attendue l’année prochaine.

>[!div class="step-by-step"]
>[Précédent](metadata.md)
>[Suivant](ws-protocols.md)
