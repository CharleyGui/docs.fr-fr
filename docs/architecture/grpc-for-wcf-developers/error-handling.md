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
# <a name="error-handling"></a>Gestion des erreurs

Windows Communication Foundation (WCF) utilise <xref:System.ServiceModel.FaultException%601> et [FaultContract](xref:System.ServiceModel.FaultContractAttribute) pour fournir des informations détaillées sur les erreurs, y compris en tenant compte de la norme SOAP Fault.

Malheureusement, la version actuelle de gRPC n’a pas la sophistication trouvée avec WCF, et n’a qu’une manipulation limitée d’erreurs intégrées basée sur des codes de statut simples et des métadonnées. Le tableau suivant est un guide rapide des codes d’état les plus couramment utilisés :

| Code d’état | Problème |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | La méthode n’a pas été écrite. |
| `GRPC_STATUS_UNAVAILABLE` | Problème avec l’ensemble du service. |
| `GRPC_STATUS_UNKNOWN` | Réponse invalide. |
| `GRPC_STATUS_INTERNAL` | Problème avec l’encodage/décodage. |
| `GRPC_STATUS_UNAUTHENTICATED` | Échec de l'authentification. |
| `GRPC_STATUS_PERMISSION_DENIED` | Échec de l’autorisation. |
| `GRPC_STATUS_CANCELLED` | L’appel a été annulé, habituellement par l’appelant. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Augmenter les erreurs dans ASP.NET Core gRPC

Un ASP.NET service Core gRPC peut envoyer une `RpcException`réponse d’erreur en jetant un , qui peut être pris par le client comme si elle était dans le même processus. Le `RpcException` doit inclure un code de statut et une description, et peut inclure optionnellement des métadonnées et un message d’exception plus long. Les métadonnées peuvent être utilisées pour `FaultContract` envoyer des données à l’appui, similaires à la façon dont les objets peuvent transporter des données supplémentaires pour les erreurs WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Attraper les erreurs chez les clients gRPC

Tout comme les clients <xref:System.ServiceModel.FaultException%601> WCF peuvent attraper des `RpcException` erreurs, un client gRPC peut attraper un pour gérer les erreurs. Parce `RpcException` que n’est pas un type générique, vous ne pouvez pas attraper différents types d’erreurs dans différents blocs. Mais vous pouvez utiliser la fonction de *filtres d’exception* de C pour déclarer des blocs distincts `catch` pour différents codes de statut, comme le montre l’exemple suivant :

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
> Lorsque vous fournissez des métadonnées supplémentaires pour les erreurs, assurez-vous de documenter les clés et les valeurs pertinentes dans votre documentation API, ou dans les commentaires dans votre `.proto` fichier.

## <a name="grpc-richer-error-model"></a>gRPC modèle d’erreur plus riche

Google a développé un [modèle d’erreur plus riche](https://cloud.google.com/apis/design/errors#error_model) qui ressemble plus à [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF , mais ce modèle n’est pas pris en charge dans C 'encore. Actuellement, il n’est disponible que pour Go, Java, Python et C.

>[!div class="step-by-step"]
>[Suivant précédent](metadata.md)
>[Next](ws-protocols.md)
