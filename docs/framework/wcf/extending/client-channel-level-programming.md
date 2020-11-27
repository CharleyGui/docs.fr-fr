---
title: Programmation au niveau du canal client
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: cf6ee310e034ad7b2e53206e1bdba68007b1a268
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275578"
---
# <a name="client-channel-level-programming"></a>Programmation au niveau du canal client

Cette rubrique explique comment écrire une application cliente Windows Communication Foundation (WCF) sans utiliser la <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> classe et son modèle objet associé.  
  
## <a name="sending-messages"></a>sending messages  

 Pour pouvoir envoyer des messages, puis recevoir et traiter les réponses, vous devez procéder comme suit :  
  
1. Créer une liaison.  
  
2. Générez une fabrication de canal.  
  
3. Créer un canal.  
  
4. Envoyez une demande et lisez la réponse.  
  
5. Fermer tous les objets de canal.  
  
#### <a name="creating-a-binding"></a>Création d’une liaison  

 Comme dans le cas de la réception (voir [programmation du Channel-Level de service](service-channel-level-programming.md)), l’envoi de messages commence par la création d’une liaison. Cet exemple crée une nouvelle liaison <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> et ajoute <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sa collection Elements.  
  
#### <a name="building-a-channelfactory"></a>Génération de ChannelFactory  

 Au lieu de créer <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, nous créons cette fois <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> en appelant <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> sur la liaison où le paramètre de type est <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Les écouteurs de canal sont utilisés par le côté qui attend les messages entrants et les fabrications de canaux le sont par le côté qui initialise la communication pour créer un canal. À l'instar des écouteurs de canal, les fabrications de canaux doivent d'abord être ouvertes avant de pouvoir être utilisées.  
  
#### <a name="creating-a-channel"></a>Création d'un canal  

 Nous appelons ensuite <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> pour créer <xref:System.ServiceModel.Channels.IRequestChannel>. Cet appel prend l'adresse du point de terminaison avec lequel nous souhaitons communiquer en utilisant le nouveau canal créé. Après avoir capté un canal, nous appelons Open sur celui-ci afin qu'il soit prêt pour la communication. Selon la nature du transport, cet appel à Open peut initialiser une connexion avec le point de terminaison cible ou peut ne rien faire du tout sur le réseau.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Envoi d'une demande et lecture de la réponse  

 Une fois un canal ouvert, nous pouvons créer un message et utiliser la méthode Request du canal pour envoyer la demande et attendre le retour de la réponse. Cette méthode retourne un message de réponse permettant de connaître la réponse du point de terminaison.  
  
#### <a name="closing-objects"></a>Fermeture des objets  

 Pour éviter la fuite des ressources, nous fermons les objets utilisés dans les communications lorsqu'ils ne sont plus nécessaires.  
  
 L'exemple de code suivant illustre un client de base utilisant la fabrication de canal pour envoyer un message et lire la réponse.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
