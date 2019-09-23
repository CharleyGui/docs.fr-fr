---
title: Points de terminaison WCF et méthodes gRPC-gRPC pour les développeurs WCF
description: Comparaison des points de terminaison WCF déclarés avec les attributs ServiceContract et OperationContract et les méthodes gRPC déclarées dans Protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184063"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Points de terminaison WCF et méthodes gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans WCF, lorsque vous écrivez le code de votre application, vous utilisez l’une des méthodes suivantes :

- Vous écrivez le code de l’application dans une classe et vous décorez les méthodes avec l’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Vous déclarez une interface pour le service et ajoutez des attributs [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à l’interface.

Par exemple, l’équivalent WCF du `greet.proto` service Greeter peut être écrit comme suit :

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Le chapitre 3 a montré que les définitions de message Protobuf sont utilisées pour générer des classes de données. Les déclarations de service et de méthode sont utilisées pour générer les classes de base que vous héritez de pour implémenter le service. Il vous suffit de déclarer les méthodes à implémenter `.proto` dans le fichier, et le compilateur génère une classe de base avec des méthodes virtuelles que vous devez substituer.

## <a name="operationcontract-properties"></a>Propriétés de OperationContract

L’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) possède des propriétés permettant de contrôler ou d’affiner son fonctionnement. les méthodes gRPC n’offrent pas ce type de contrôle. Le tableau suivant définit ces `OperationContract` propriétés et comment les fonctionnalités qu’elles spécifient sont (ou ne sont pas) traitées dans gRPC :

| Propriété`OperationContract` | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | URI identifiant l’opération. gRPC `package`utilise le nom du `service` et `rpc` `.proto` du fichier. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Toutes les méthodes de service `Task` gRPC retournent des objets. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Voir la remarque ci-dessous. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Les méthodes gRPC à sens unique `Empty` renvoient des résultats ou utilisent la diffusion en continu du client. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Voir la remarque ci-dessous. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Lié à SOAP, aucune signification dans gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Aucun chiffrement de message ; le chiffrement réseau est géré au niveau de la couche de transport (TLS sur HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Lié à SOAP, aucune signification dans gRPC. |

La `IsInitiating` propriété vous permet d’indiquer qu’une méthode dans un [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) ne peut pas être la première méthode appelée dans le cadre d’une session. La `IsTerminating` propriété force le serveur à fermer la session après l’appel d’une opération (ou le client, s’il est utilisé sur un client de rappel). Dans gRPC, les flux sont créés par des méthodes uniques et fermés explicitement. Consultez [diffusion en continu gRPC](rpc-types.md#grpc-streaming).

Pour plus d’informations sur la sécurité et le chiffrement gRPC, consultez le [chapitre 6](security.md).

>[!div class="step-by-step"]
>[Précédent](wcf-services-to-grpc-comparison.md)
>[Suivant](wcf-bindings.md)
