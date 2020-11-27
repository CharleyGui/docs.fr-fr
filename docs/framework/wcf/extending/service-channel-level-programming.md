---
title: Programmation de service au niveau du canal
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: db50d385bd396ba4de74e08fc1c6d93a67f320b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290216"
---
# <a name="service-channel-level-programming"></a>Programmation de service au niveau du canal

Cette rubrique explique comment écrire une application de service Windows Communication Foundation (WCF) sans utiliser le <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> et son modèle objet associé.  
  
## <a name="receiving-messages"></a>réception de messages  

 Pour pouvoir recevoir et traiter des messages, vous devez effectuer les étapes suivantes :  
  
1. Créer une liaison.  
  
2. Générer un écouteur de canal.  
  
3. Ouvrir l'écouteur de canal.  
  
4. Lire la demande et envoyer une réponse.  
  
5. Fermer tous les objets de canal.  
  
#### <a name="creating-a-binding"></a>Création d’une liaison  

 La première étape pour écouter et recevoir des messages consiste à créer une liaison. WCF est fourni avec plusieurs liaisons intégrées ou fournies par le système qui peuvent être utilisées directement en instanciant l’une d’entre elles. Vous pouvez également créer votre propre liaison personnalisée en instanciant une classe CustomBinding, comme dans le code n°1.  
  
 L’exemple de code suivant crée une instance de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> et ajoute un <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sa collection Elements qui est une collection d’éléments de liaison utilisés pour générer la pile de canaux. Dans cet exemple, la collection d'éléments ayant uniquement le <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, la pile de canaux résultante dispose uniquement du canal de transport HTTP.  
  
#### <a name="building-a-channellistener"></a>Génération d'un ChannelListener  

 Après avoir créé une liaison, nous appelons <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> pour générer l'écouteur de canal où le paramètre de type est la forme de canal à créer. Dans cet exemple, nous utilisons <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> car nous souhaitons écouter les messages entrants dans un modèle d'échange de messages demande/réponse.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> est utilisé pour recevoir des messages de demande et renvoyer des messages de réponse. <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> retourne un <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, qui peut être utilisé pour recevoir le message de demande et renvoyer un message de réponse.  
  
 Lors de la création de l'écouteur, nous passons l'adresse réseau sur laquelle il écoute, en l'occurrence `http://localhost:8080/channelapp`. En général, chaque canal de transport prend en charge un ou plusieurs schémas d'adressage ; le transport HTTP, par exemple, prend en charge les schémas http et https.  
  
 Nous passons également un <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> vide lors de la création de l'écouteur. Un paramètre de liaison est un mécanisme permettant de passer des paramètres qui contrôlent la manière dont l’écouteur doit être généré. Dans notre exemple, nous n’utilisons pas de tels paramètres ; nous passons donc une collection vide.  
  
#### <a name="listening-for-incoming-messages"></a>Écoute des messages entrants  

 Nous appelons ensuite <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur l'écouteur et nous commençons à accepter des canaux. Le comportement de <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> varie selon que le transport est orienté connexion ou sans connexion. Pour les transports orientés connexion, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> se bloque jusqu'à ce qu'une nouvelle demande de connexion arrive, auquel point il retourne un nouveau canal qui représente cette nouvelle connexion. Pour les transports sans connexion, tels que HTTP, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> est retourné immédiatement avec l'unique canal que l'écouteur de transport crée.  
  
 Dans cet exemple, l'écouteur retourne un canal qui implémente <xref:System.ServiceModel.Channels.IReplyChannel>. Pour recevoir des messages sur ce canal, nous appelons d'abord <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur lui afin de le placer dans un état prêt pour la communication. Nous appelons ensuite <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A>, qui se bloque jusqu'à ce qu'un message arrive.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Lecture de la demande et envoi de la réponse  

 Lorsque <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> retourne un <xref:System.ServiceModel.Channels.RequestContext>, nous obtenons le message reçu à l'aide de sa propriété <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A>. Nous écrivons l'action et le contenu du corps du message (que nous supposons être une chaîne).  
  
 Pour envoyer une réponse, nous créons un message de réponse ; en l'occurrence, nous repassons les données de chaîne que nous avons reçues dans la demande. Nous appelons ensuite <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> pour envoyer le message de réponse.  
  
#### <a name="closing-objects"></a>Fermeture des objets  

 Pour éviter toute fuite des ressources, il est très important de fermer les objets utilisés dans les communications lorsqu'ils ne sont plus nécessaires. Dans cet exemple, nous fermons le message de demande, le contexte de demande, le canal et l'écouteur.  
  
 L'exemple de code suivant illustre un service de base dans lequel un écouteur de canal reçoit un seul message. Un vrai service continue à accepter des canaux et à recevoir des messages jusqu'à ce que le service s'arrête.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
