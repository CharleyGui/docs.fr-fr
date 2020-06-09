---
title: Activités de messagerie
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 69a0e9a415b10d9c58d04eac27e48b1ed6a78064
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576393"
---
# <a name="messaging-activities"></a>Activités de messagerie

Les activités de messagerie permettent aux workflows d'envoyer et de recevoir des messages WCF. En ajoutant des activités de messagerie à un workflow, vous pouvez modéliser n'importe quel modèle d'échange de messages (MEP) arbitrairement complexe.

## <a name="message-exchange-patterns"></a>Modèles d’échange de messages

Il existe trois modèles d'échange de messages de base :

- **Datagramme** : lors de l’utilisation du datagramme MEP, le client envoie un message au service, mais le service ne répond pas. Cet échange est parfois appelé « fire and forget ». Un échange de ce type requiert une confirmation hors bande de la réussite de la remise. Le message peut être perdu lors de la transmission et ne jamais atteindre le service. Si le client envoie un message avec succès, cela ne garantit pas que le service a reçu le message. Le datagramme est un bloc de construction de messagerie fondamental. Vous pouvez en effet générer vos propres MEP au-dessus de ce bloc.

- **Demande-réponse** : lors de l’utilisation du MEP de requête-réponse, le client envoie un message au service, le service effectue le traitement requis, puis renvoie une réponse au client. Ce modèle se compose de paires demande-réponse. Parmi les exemples d'appels demande-réponse figurent notamment les appels de procédure distante (RPC) et les demandes GET de navigateur. Ce modèle est également connu sous le nom de mode semi-duplex.

- **Duplex** : lors de l’utilisation du MEP duplex, le client et le service peuvent envoyer des messages entre eux dans n’importe quel ordre. Le MEP duplex est similaire à une conversation téléphonique, où chaque mot prononcé correspond à un message.

Les activités de messagerie vous permettent d'implémenter chacun de ces MEP de base ainsi qu'un MEP arbitrairement complexe.

## <a name="messaging-activities"></a>Activités de messagerie

Le [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] définit les activités de messagerie suivantes :

- <xref:System.ServiceModel.Activities.Send> : utilise l'activité <xref:System.ServiceModel.Activities.Send> pour envoyer un message.

- <xref:System.ServiceModel.Activities.SendReply> : utilise l'activité <xref:System.ServiceModel.Activities.SendReply> pour envoyer une réponse à un message reçu. Cette activité est utilisée par les services de workflow lors de l'implémentation d'un MEP demande/réponse.

- <xref:System.ServiceModel.Activities.Receive> : utilise l'activité <xref:System.ServiceModel.Activities.Receive> pour recevoir un message.

- <xref:System.ServiceModel.Activities.ReceiveReply> : utilise l'activité <xref:System.ServiceModel.Activities.ReceiveReply> pour recevoir un message de réponse. Cette activité est utilisée par les clients du service de workflow lors de l'implémentation d'un MEP demande/réponse.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Activités de messagerie et modèles d’échange de messages

Un MEP datagramme implique un client qui envoie un message et un service qui reçoit le message. Si le client est un workflow, utilisez une activité <xref:System.ServiceModel.Activities.Send> pour envoyer le message. Pour recevoir ce message dans un workflow, utilisez une activité <xref:System.ServiceModel.Activities.Receive>. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> ont chacune une propriété nommée `Content`. Cette propriété contient les données qui sont envoyées ou reçues. Lors de l'implémentation du MEP demande-réponse, le client et le service utilisent tous les deux des paires d'activités. Le client utilise une activité <xref:System.ServiceModel.Activities.Send> pour envoyer le message et une activité <xref:System.ServiceModel.Activities.ReceiveReply> pour recevoir la réponse du service. Ces deux activités sont associées l'une à l'autre par la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>. Cette propriété est définie sur l'activité <xref:System.ServiceModel.Activities.Send> qui a envoyé le message d'origine. Le service utilise également une paire d'activités associées : <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>. Ces deux activités sont associées par la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A>. Cette propriété est définie sur l'activité <xref:System.ServiceModel.Activities.Receive> qui a reçu le message d'origine. Les activités <xref:System.ServiceModel.Activities.ReceiveReply> et <xref:System.ServiceModel.Activities.SendReply>, comme <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> vous permettent d'envoyer une instance <xref:System.ServiceModel.Channels.Message> ou un type de contrat de message.

En raison de la longue durée d’exécution des workflows, il est important que le modèle duplex de communication prenne également en charge des conversations de longue durée. Pour prendre en charge des conversations de longue durée, les clients qui initialisent la conversation doivent donner au service la possibilité de le rappeler plus tard lorsque les données deviennent disponibles. Par exemple, une demande de bon de commande est soumise à l'approbation du gestionnaire, mais elle risque de ne pas être traitée dans la journée, la semaine ou même l'année ; le workflow qui gère l'approbation du bon de commande doit le savoir pour continuer une fois l'approbation donnée. Ce modèle de communication en duplex est pris en charge dans les workflows à l'aide de la corrélation. Pour implémenter un modèle duplex, utilisez les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive>. Sur l' <xref:System.ServiceModel.Activities.Receive> activité, initialisez une corrélation à l’aide de <xref:System.ServiceModel.Activities.CorrelationHandle> . Sur l'activité <xref:System.ServiceModel.Activities.Send>, définissez ce gestionnaire de corrélation comme valeur de la propriété <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>. Pour plus d’informations, consultez [duplex durable](durable-duplex-correlation.md).

> [!NOTE]
> L’implémentation du flux de travail du duplex à l’aide d’une corrélation de rappel (« duplex durable ») est destinée aux conversations de longue durée. Ce n'est pas la même chose qu'un duplex WCF avec des contrats de rappel, où la conversation est de courte durée d'exécution (durée de vie du canal).

## <a name="message-formatting-and-messaging-activities"></a>Mise en forme des messages et activités de messagerie

Les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.ReceiveReply> ont une propriété nommée `Content`. Cette propriété est de type <xref:System.ServiceModel.Activities.ReceiveContent> et représente les données que reçoit l'activité <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.ReceiveReply>. Le .NET Framework définit deux classes connexes nommées <xref:System.ServiceModel.Activities.ReceiveMessageContent> et <xref:System.ServiceModel.Activities.ReceiveParametersContent> qui sont toutes les deux dérivées de <xref:System.ServiceModel.Activities.ReceiveContent>. Définissez la propriété <xref:System.ServiceModel.Activities.Receive> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> ou `Content` sur une instance de l'un de ces types pour recevoir des données dans un service de workflow. Le type à utiliser dépend du type des données que l'activité reçoit. Si l'activité reçoit un objet `Message` ou un type de contrat de message, utilisez <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Si l'activité accepte un jeu de contrats de données ou de types XML qui peut être sérialisé, utilisez <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> vous permet d'envoyer plusieurs paramètres, alors que <xref:System.ServiceModel.Activities.ReceiveMessageContent> vous permet uniquement d'envoyer un objet, le message (ou le type de contrat de message).

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent> peut également être utilisé avec un contrat de données ou un type XML unique qui peut être sérialisé. La différence entre utiliser <xref:System.ServiceModel.Activities.ReceiveParametersContent> avec un paramètre unique et l'objet transmis directement à <xref:System.ServiceModel.Activities.ReceiveMessageContent> est le format de câble. Le contenu du paramètre est encapsulé dans un élément XML correspondant au nom de l'opération et l'objet sérialisé est encapsulé dans un élément XML à l'aide du nom de paramètre (par exemple, `<Echo><msg>Hello, World</msg></Echo>`). Le contenu du message n'est pas encapsulé par le nom de l'opération. L'objet sérialisé est en revanche placé dans un élément XML à l'aide du nom de type qualifié XML (par exemple, `<string>Hello, World</string>`).

Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.SendReply> ont également une propriété nommée `Content`. Cette propriété est de type <xref:System.ServiceModel.Activities.SendContent> et représente les données envoyées par l'activité <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply>. Le .NET Framework définit deux types connexes nommés <xref:System.ServiceModel.Activities.SendMessageContent> et <xref:System.ServiceModel.Activities.SendParametersContent> qui sont tous les deux dérivés de <xref:System.ServiceModel.Activities.SendContent>. Définissez la propriété <xref:System.ServiceModel.Activities.Send> de l'activité <xref:System.ServiceModel.Activities.SendReply> ou `Content` sur une instance de l'un de ces types pour envoyer des données à partir d'un service de workflow. Le type à utiliser dépend du type de données que l'activité envoie. Si l'activité envoie un objet `Message` ou un type de contrat de message, utilisez <xref:System.ServiceModel.Activities.SendMessageContent>. Si l'activité envoie un type de contrat de données, utilisez <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> vous permet d'envoyer plusieurs paramètres, alors que <xref:System.ServiceModel.Activities.SendMessageContent> vous permet uniquement d'envoyer un objet, le message (ou le type de contrat de message).

Lorsque vous programmez de façon impérative avec les activités de messagerie, vous utilisez les <xref:System.Activities.InArgument%601> et <xref:System.Activities.OutArgument%601> génériques pour encapsuler les objets que vous affectez au message ou les propriétés de paramètres des activités <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.ReceiveReply>. Utilisez <xref:System.Activities.InArgument%601> pour les <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> activités et, ainsi que <xref:System.Activities.OutArgument%601> pour les activités et <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> . Les arguments `In` sont utilisés avec les activités d'envoi, car les données sont passées dans les activités. Les arguments `Out` sont utilisés avec les activités d'envoi, car les données sont transmises dans les activités, comme indiqué dans l'exemple suivant.

```csharp
Receive reserveSeat = new Receive
{
    ...
    Content = new ReceiveParametersContent
    {
        Parameters =
        {
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }
        }
    }
};
SendReply reserveSeat = new SendReply
{
    ...
    Request = reserveSeat,
    Content = new SendParametersContent
    {
        Parameters =
        {
            { "ReservationId", new InArgument<string>(reservationId) }
        }
    },
};
```

Lors de l'implémentation d'un service de workflow définissant une opération de demande/réponse qui retourne void, vous devez instancier une activité <xref:System.ServiceModel.Activities.SendReply> et définir la propriété <xref:System.ServiceModel.Activities.SendReply.Content%2A> sur une instance vide de l'un des types de contenu (<xref:System.ServiceModel.Activities.SendMessageContent> ou <xref:System.ServiceModel.Activities.SendParametersContent>), comme indiqué dans l'exemple suivant.

```csharp
Receive rcv = new Receive()
{
ServiceContractName = "IService",
OperationName = "NullReturningContract",
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )
};
SendReply sr = new SendReply()
{
Request = rcv
   Content = new SendParametersContent();
};
```

## <a name="add-service-reference"></a>Ajouter une référence de service

Lors de l’appel d’un service de workflow à partir d’une application de flux de travail, Visual Studio 2012 génère des activités de messagerie personnalisées qui encapsulent les <xref:System.ServiceModel.Activities.Send> activités et habituelles <xref:System.ServiceModel.Activities.ReceiveReply> utilisées dans un MEP de demande/réponse. Pour utiliser cette fonctionnalité, cliquez avec le bouton droit sur le projet client dans Visual Studio, puis sélectionnez **Ajouter**une  >  **référence de service**. Tapez l'adresse de base du service dans la zone d'adresse et cliquez sur OK. Les services disponibles s’affichent dans la zone **services :** . Développez le nœud du service pour afficher les contrats pris en charge. Sélectionnez le contrat que vous souhaitez appeler et la liste des opérations disponibles s’affiche dans la zone **opérations** . Vous pouvez ensuite spécifier l’espace de noms de l’activité générée, puis cliquer sur **OK**. Un dialogue s'affiche indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées se trouveront dans la boîte à outils une fois le projet reconstruit. Il existe une activité pour chaque opération définie sur le contrat de service. Après avoir reconstruit le projet, vous pouvez faire glisser et déposer les activités personnalisées sur votre workflow et définir les propriétés nécessaires dans la fenêtre de propriétés.

## <a name="messaging-activity-templates"></a>Modèles d’activité de messagerie

Pour faciliter la configuration d’un MEP de demande/réponse sur le client et le service, Visual Studio 2012 fournit deux modèles d’activité de messagerie. `System.ServiceModel.Activities.Design.ReceiveAndSendReply` est utilisé sur le service et `System.ServiceModel.Activities.Design.SendAndReceiveReply` est utilisé sur le client. Dans les deux cas, les modèles ajoutent les activités de messagerie appropriées à votre workflow. Sur le service, le modèle `System.ServiceModel.Activities.Design.ReceiveAndSendReply` ajoute une activité <xref:System.ServiceModel.Activities.Receive> suivie d'une activité <xref:System.ServiceModel.Activities.SendReply>. La propriété <xref:System.ServiceModel.Activities.SendReply.Request> est automatiquement définie sur l'activité <xref:System.ServiceModel.Activities.Receive>. Sur le client, le modèle `System.ServiceModel.Activities.Design.SendAndReceiveReply` ajoute une activité <xref:System.ServiceModel.Activities.Send> suivie d'une activité <xref:System.ServiceModel.Activities.ReceiveReply>. La propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> est automatiquement définie sur l'activité <xref:System.ServiceModel.Activities.Send>. Pour utiliser ces modèles, il suffit de glisser-déposer le modèle approprié sur votre workflow.

## <a name="messaging-activities-and-transactions"></a>Activités et transactions de messagerie

Lorsqu’un appel est effectué à un service de workflow, vous pouvez souhaiter transmettre une transaction à l’opération de service. Pour cela, placez l'activité <xref:System.ServiceModel.Activities.Receive> dans une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. L'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> contient une activité `Receive` et un corps. La transaction transmise au service reste ambiante pendant l’exécution du corps de l’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. La transaction se termine une fois l’exécution du corps terminée. Pour plus d’informations sur les workflows et les transactions, consultez [transactions de workflow](../../windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Voir aussi

- [Envoyer et recevoir des erreurs dans les services de workflow](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Création d'un service de workflow de longue durée](creating-a-long-running-workflow-service.md)
