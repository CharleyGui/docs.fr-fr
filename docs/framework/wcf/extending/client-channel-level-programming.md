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
# <a name="client-channel-level-programming"></a><span data-ttu-id="da498-102">Programmation au niveau du canal client</span><span class="sxs-lookup"><span data-stu-id="da498-102">Client Channel-Level Programming</span></span>

<span data-ttu-id="da498-103">Cette rubrique explique comment écrire une application cliente Windows Communication Foundation (WCF) sans utiliser la <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> classe et son modèle objet associé.</span><span class="sxs-lookup"><span data-stu-id="da498-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="da498-104">sending messages</span><span class="sxs-lookup"><span data-stu-id="da498-104">Sending Messages</span></span>  

 <span data-ttu-id="da498-105">Pour pouvoir envoyer des messages, puis recevoir et traiter les réponses, vous devez procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="da498-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="da498-106">Créer une liaison.</span><span class="sxs-lookup"><span data-stu-id="da498-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="da498-107">Générez une fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="da498-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="da498-108">Créer un canal.</span><span class="sxs-lookup"><span data-stu-id="da498-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="da498-109">Envoyez une demande et lisez la réponse.</span><span class="sxs-lookup"><span data-stu-id="da498-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="da498-110">Fermer tous les objets de canal.</span><span class="sxs-lookup"><span data-stu-id="da498-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="da498-111">Création d’une liaison</span><span class="sxs-lookup"><span data-stu-id="da498-111">Creating a Binding</span></span>  

 <span data-ttu-id="da498-112">Comme dans le cas de la réception (voir [programmation du Channel-Level de service](service-channel-level-programming.md)), l’envoi de messages commence par la création d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="da498-112">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="da498-113">Cet exemple crée une nouvelle liaison <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> et ajoute <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sa collection Elements.</span><span class="sxs-lookup"><span data-stu-id="da498-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="da498-114">Génération de ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="da498-114">Building a ChannelFactory</span></span>  

 <span data-ttu-id="da498-115">Au lieu de créer <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, nous créons cette fois <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> en appelant <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> sur la liaison où le paramètre de type est <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da498-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="da498-116">Les écouteurs de canal sont utilisés par le côté qui attend les messages entrants et les fabrications de canaux le sont par le côté qui initialise la communication pour créer un canal.</span><span class="sxs-lookup"><span data-stu-id="da498-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="da498-117">À l'instar des écouteurs de canal, les fabrications de canaux doivent d'abord être ouvertes avant de pouvoir être utilisées.</span><span class="sxs-lookup"><span data-stu-id="da498-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="da498-118">Création d'un canal</span><span class="sxs-lookup"><span data-stu-id="da498-118">Creating a Channel</span></span>  

 <span data-ttu-id="da498-119">Nous appelons ensuite <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> pour créer <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="da498-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="da498-120">Cet appel prend l'adresse du point de terminaison avec lequel nous souhaitons communiquer en utilisant le nouveau canal créé.</span><span class="sxs-lookup"><span data-stu-id="da498-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="da498-121">Après avoir capté un canal, nous appelons Open sur celui-ci afin qu'il soit prêt pour la communication.</span><span class="sxs-lookup"><span data-stu-id="da498-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="da498-122">Selon la nature du transport, cet appel à Open peut initialiser une connexion avec le point de terminaison cible ou peut ne rien faire du tout sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="da498-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="da498-123">Envoi d'une demande et lecture de la réponse</span><span class="sxs-lookup"><span data-stu-id="da498-123">Sending a Request and Reading the Reply</span></span>  

 <span data-ttu-id="da498-124">Une fois un canal ouvert, nous pouvons créer un message et utiliser la méthode Request du canal pour envoyer la demande et attendre le retour de la réponse.</span><span class="sxs-lookup"><span data-stu-id="da498-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="da498-125">Cette méthode retourne un message de réponse permettant de connaître la réponse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="da498-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="da498-126">Fermeture des objets</span><span class="sxs-lookup"><span data-stu-id="da498-126">Closing Objects</span></span>  

 <span data-ttu-id="da498-127">Pour éviter la fuite des ressources, nous fermons les objets utilisés dans les communications lorsqu'ils ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="da498-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="da498-128">L'exemple de code suivant illustre un client de base utilisant la fabrication de canal pour envoyer un message et lire la réponse.</span><span class="sxs-lookup"><span data-stu-id="da498-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
