---
title: Envoi et réception des erreurs
description: Découvrez comment un service ou un client duplex peut envoyer des erreurs SOAP lorsqu’une condition d’erreur se produit et comment un client ou une application de service gère ces erreurs.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 23f63fde2755a29cd545d3aefe699cad8dbecb3b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244320"
---
# <a name="sending-and-receiving-faults"></a>Envoi et réception des erreurs

Les erreurs SOAP acheminent des informations de condition d'erreur d'un service à un client et, dans le cas duplex, d'un client à un service d'une manière interopérable. En général un service définit le contenu des erreurs personnalisées et spécifie quelles opérations peuvent les retourner. (Pour plus d’informations, consultez [définition et spécification des erreurs](defining-and-specifying-faults.md).) Cette rubrique explique comment un service ou un client duplex peut envoyer ces Erreurs lorsque la condition d’erreur correspondante s’est produite et comment un client ou une application de service gère ces erreurs. Pour obtenir une vue d’ensemble de la gestion des erreurs dans les applications Windows Communication Foundation (WCF), consultez [spécification et gestion des erreurs dans les contrats et les services](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="sending-soap-faults"></a>Envoi d'erreurs SOAP

Les erreurs SOAP déclarées sont celles dans lesquelles une opération contient un <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> qui spécifie un type d'erreur SOAP personnalisé. Les erreurs SOAP non déclarées sont celles qui ne sont pas spécifiées dans le contrat d'une opération.

### <a name="sending-declared-faults"></a>Envoi d'erreurs déclarées

Pour envoyer une erreur SOAP déclarée, détectez la condition d'erreur pour laquelle l'erreur SOAP est appropriée et levez une nouvelle <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> où le paramètre de type est un nouvel objet du type spécifié dans le <xref:System.ServiceModel.FaultContractAttribute> pour cette opération. L'exemple de code suivant illustre l'utilisation de <xref:System.ServiceModel.FaultContractAttribute> pour spécifier que l'opération `SampleMethod` peut retourner une erreur SOAP avec le type de détail `GreetingFault`.

[!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
[!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

Pour acheminer les informations sur l'erreur `GreetingFault` au client, interceptez la condition d'erreur appropriée et levez une nouvelle <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> de type `GreetingFault` avec un nouvel objet `GreetingFault` comme argument, comme dans l'exemple de code suivant. Si le client est une application cliente WCF, il rencontre cette erreur en tant qu’exception managée où le type est <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> de type `GreetingFault` .

[!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
[!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

### <a name="sending-undeclared-faults"></a>Envoi d'erreurs non déclarées

L’envoi d’erreurs non déclarées peut être très utile pour diagnostiquer et déboguer rapidement les problèmes dans les applications WCF, mais son utilité en tant qu’outil de débogage est limitée. Plus généralement, lors du débogage il est recommandé d'utiliser la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>. Lorsque vous définissez cette valeur à « true », les clients rencontrent des erreurs telles que des exceptions <xref:System.ServiceModel.FaultException%601> de type <xref:System.ServiceModel.ExceptionDetail>.

> [!IMPORTANT]
> Étant donné que les exceptions managées peuvent exposer des informations d’application internes, le paramétrage <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> `true` peut permettre aux clients WCF d’obtenir des informations sur les exceptions d’opération de service internes, y compris l’identification personnelle ou d’autres informations sensibles.
>
> Par conséquent, l'affectation de la valeur <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> à <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou `true` est uniquement recommandée comme une façon de déboguer temporairement une application de service. De plus, le WSDL pour une méthode qui retourne des exceptions managées non prises en charge de cette façon ne contient pas le contrat pour le <xref:System.ServiceModel.FaultException%601> de type <xref:System.ServiceModel.ExceptionDetail>. Les clients doivent attendre une erreur SOAP inconnue (retournée aux clients WCF en tant qu' <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objets) pour obtenir correctement les informations de débogage.

Pour envoyer une erreur SOAP non déclarée, levez un objet <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> (autrement dit, pas le type générique <xref:System.ServiceModel.FaultException%601>) et passez la chaîne au constructeur. Cela est exposé aux applications clientes WCF en tant qu' <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> exception levée lorsque la chaîne est disponible en appelant la <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> méthode.

> [!NOTE]
> Si vous déclarez une erreur SOAP de type chaîne et que vous la levez ensuite dans votre service en tant que <xref:System.ServiceModel.FaultException%601> où le paramètre de type est un <xref:System.String?displayProperty=nameWithType>, la valeur de chaîne est assignée à la propriété <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> et n'est pas disponible à partir de <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.

## <a name="handling-faults"></a>Gestion des erreurs

Dans les clients WCF, les erreurs SOAP qui se produisent pendant la communication qui présentent un intérêt pour les applications clientes sont levées en tant qu’exceptions managées. Bien qu’il existe de nombreuses exceptions qui peuvent se produire pendant l’exécution d’un programme, les applications utilisant le modèle de programmation client WCF peuvent s’attendre à gérer les exceptions des deux types suivants à la suite de la communication.

- <xref:System.TimeoutException>

- <xref:System.ServiceModel.CommunicationException>

Les objets <xref:System.TimeoutException> sont levés lorsqu'une opération dépasse le délai d'attente spécifié.

Les objets <xref:System.ServiceModel.CommunicationException> sont levés lorsqu'il existe une condition d'erreur de communication récupérable sur le service ou le client.

La classe <xref:System.ServiceModel.CommunicationException> a deux types dérivés importants, <xref:System.ServiceModel.FaultException> et le type <xref:System.ServiceModel.FaultException%601> générique.

Les exceptions <xref:System.ServiceModel.FaultException> sont levées lorsqu'un écouteur reçoit une erreur inattendue ou qui n'est spécifiée dans le contrat d'opération ; habituellement, cela se produit lorsque l'application est déboguée et que le service a la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> définie à `true`.

Les exceptions <xref:System.ServiceModel.FaultException%601> sont levées sur le client lorsqu'une erreur spécifiée dans le contrat d'opération est reçue en réponse à une opération bidirectionnelle (autrement dit, une méthode avec un attribut <xref:System.ServiceModel.OperationContractAttribute> ayant la valeur <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> affectée à la propriété `false`).

> [!NOTE]
> Lorsqu’un service WCF a la <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriété ou définie sur `true` le client se comporte comme un non déclaré <xref:System.ServiceModel.FaultException%601> de type <xref:System.ServiceModel.ExceptionDetail> . Les clients peuvent intercepter cette erreur spécifique ou gérer l'erreur dans un bloc catch pour <xref:System.ServiceModel.FaultException>.

En général, seules les exceptions <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException> et <xref:System.ServiceModel.CommunicationException> sont dignes d'intérêt pour les clients et les services.

> [!NOTE]
> D'autres exceptions, bien sûr, se produisent. Les exceptions inattendues incluent des défaillances catastrophiques telles que <xref:System.OutOfMemoryException?displayProperty=nameWithType> ; en général, les applications ne doivent pas intercepter de telles méthodes.

### <a name="catch-fault-exceptions-in-the-correct-order"></a>Interception des exceptions dans l'ordre correct

Étant donné que <xref:System.ServiceModel.FaultException%601> dérive de <xref:System.ServiceModel.FaultException> et que <xref:System.ServiceModel.FaultException> dérive de <xref:System.ServiceModel.CommunicationException>, il est important d'intercepter ces exceptions dans l'ordre approprié. Si, par exemple, vous avez un bloc try/catch dans lequel vous interceptez d'abord <xref:System.ServiceModel.CommunicationException>, toutes les erreurs SOAP spécifiées et non spécifiées sont gérées à cet emplacement ; les blocs catch suivants destinés à gérer une exception <xref:System.ServiceModel.FaultException%601> personnalisée ne sont jamais appelés.

Souvenez-vous qu'une opération peut retourner une quantité d'erreurs spécifiées quelconque. Chaque erreur est un type unique et doit être gérée séparément.

### <a name="handle-exceptions-when-closing-the-channel"></a>Gestion des exceptions lors de la fermeture du canal

La majeure partie de la discussion précédente concerne les erreurs envoyées au cours du traitement des messages d’application, autrement dit, les messages envoyés explicitement par le client lorsque l’application cliente appelle des opérations sur l’objet client WCF.

Même avec les objets locaux, l'élimination de l'objet peut déclencher ou masquer des exceptions qui se produisent pendant le processus de recyclage. Un résultat similaire peut se produire lorsque vous utilisez des objets clients WCF. Lorsque vous appelez des opérations, vous envoyez des messages sur une connexion établie. La fermeture du canal peut lever des exceptions si la connexion ne peut pas être fermée proprement ou si elle est déjà fermée, même si toutes les opérations ont été retournées correctement.

En général, les canaux d'objets clients sont fermés dans les cas suivants :

- Lorsque l’objet client WCF est recyclé.

- Lorsque l'application cliente appelle <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.

- Lorsque l'application cliente appelle <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.

- Lorsque l'application cliente appelle une opération qui est une opération de fin pour une session.

Dans tous les cas, la fermeture du canal fait en sorte que celui-ci commence à fermer tous les canaux sous-jacents qui peuvent envoyer des messages pour prendre en charge la fonctionnalité complexe au niveau application. Par exemple, lorsqu’un contrat requiert des sessions, une liaison tente d’établir une session en échangeant des messages avec le canal de service jusqu’à ce qu’une session soit établie. Lorsque le canal est fermé, le canal de session sous-jacent signale au service que la session est terminée. Dans ce cas, si le canal a déjà abandonné, est déjà fermé ou est inutilisable (par exemple, lorsqu'un câble réseau est débranché), le canal client ne peut pas signaler au canal de service que la session est terminée et une exception peut être déclenchée.

### <a name="abort-the-channel-if-necessary"></a>Abandon du canal si nécessaire

La fermeture du canal pouvant également lever des exceptions, en plus d'intercepter les exceptions dans l'ordre correct il est important d'abandonner le canal utilisé pour effectuer l'appel dans le bloc catch.

Si l'erreur achemine des informations d'erreur spécifiques à une opération et qu'il est encore possible que d'autres puissent l'utiliser, il n'est pas nécessaire d'abandonner le canal (bien que ces cas soient rares). Dans tous les autres cas, il est recommandé d'abandonner le canal. Pour obtenir un exemple qui illustre tous ces points, consultez [exceptions attendues](./samples/expected-exceptions.md).

L'exemple de code suivant indique comment gérer des exceptions SOAP dans une application cliente de base, y compris une erreur déclarée et une erreur non déclarée.

> [!NOTE]
> Cet exemple de code n'utilise pas la construction `using`. Étant donné que la fermeture des canaux peut lever des exceptions, il est recommandé que les applications créent d’abord un client WCF, puis ouvrent, utilisent et ferment le client WCF dans le même bloc try. Pour plus d’informations, consultez [vue d’ensemble du client WCF](wcf-client-overview.md) et [utilisation de Close et Abort pour libérer des ressources clientes WCF](./samples/use-close-abort-release-wcf-client-resources.md).

[!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
[!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Expected Exceptions](./samples/expected-exceptions.md)
- [Utiliser la fermeture et l’abandon pour libérer des ressources de client WCF](./samples/use-close-abort-release-wcf-client-resources.md)
