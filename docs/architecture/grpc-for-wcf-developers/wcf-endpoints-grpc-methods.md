---
title: Points de terminaison WCF et méthodes gRPC-gRPC pour les développeurs WCF
description: Comparaison des points de terminaison WCF déclarés avec les attributs ServiceContract et OperationContract et les méthodes gRPC déclarées dans Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503433"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Points de terminaison WCF et méthodes gRPC

Dans Windows Communication Foundation (WCF), lorsque vous écrivez le code de votre application, vous utilisez l’une des méthodes suivantes :

- Vous écrivez le code de l’application dans une classe et vous décorez les méthodes avec l’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Vous déclarez une interface pour le service et ajoutez des attributs [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à l’interface.

Par exemple, l’équivalent WCF du service `greet.proto` Greeter peut être écrit comme suit :

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Le chapitre 3 a montré que les définitions de message Protobuf sont utilisées pour générer des classes de données. Les déclarations de service et de méthode sont utilisées pour générer les classes de base que vous héritez de pour implémenter le service. Il vous suffit de déclarer les méthodes à implémenter dans le fichier `.proto`, et le compilateur génère une classe de base avec des méthodes virtuelles que vous devez substituer.

## <a name="operationcontract-properties"></a>Propriétés de OperationContract

L’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) possède des propriétés permettant de contrôler ou d’affiner son fonctionnement. les méthodes gRPC n’offrent pas ce type de contrôle. Le tableau suivant répertorie ces propriétés de `OperationContract` et décrit comment les fonctionnalités qu’elles spécifient sont (ou ne sont pas) traitées dans gRPC :

| Propriété `OperationContract` | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Un URI identifie l’opération. gRPC utilise le nom de `package`, `service`et `rpc` dans le fichier `.proto`. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Toutes les méthodes de service gRPC retournent des objets `Task`. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Consultez le paragraphe après ce tableau. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Les méthodes gRPC à sens unique retournent `Empty` résultats ou utilisent la diffusion en continu du client. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Consultez le paragraphe après ce tableau. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Cette propriété est liée à SOAP et n’a aucune signification dans gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Il n’y a pas de chiffrement des messages. Le chiffrement réseau est géré au niveau de la couche de transport (TLS sur HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Cette propriété est liée à SOAP et n’a aucune signification dans gRPC. |

La propriété `IsInitiating` vous permet d’indiquer qu’une méthode dans [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) ne peut pas être la première méthode appelée dans le cadre d’une session. La propriété `IsTerminating` oblige le serveur à fermer la session après l’appel d’une opération (ou le client, si la propriété est utilisée sur un client de rappel). Dans gRPC, les flux sont créés par des méthodes uniques et fermés explicitement. Consultez [diffusion en continu gRPC](rpc-types.md#grpc-streaming).

Pour plus d’informations sur la sécurité et le chiffrement gRPC, consultez le [chapitre 6](security.md).

>[!div class="step-by-step"]
>[Précédent](wcf-services-to-grpc-comparison.md)
>[Suivant](wcf-bindings.md)
