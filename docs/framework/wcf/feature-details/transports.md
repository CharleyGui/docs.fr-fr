---
title: Transports dans Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 8623b788b848867f25836a657b07349dd50c2780
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251683"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="8dee9-102">Transports dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8dee9-102">Transports in Windows Communication Foundation</span></span>

<span data-ttu-id="8dee9-103">La couche de transport se situe au niveau le plus bas de la pile des canaux.</span><span class="sxs-lookup"><span data-stu-id="8dee9-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="8dee9-104">Les transports principaux utilisés dans Windows Communication Foundation (WCF) sont HTTP, HTTPs, TCP et les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="8dee9-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="8dee9-105">Les rubriques de cette section contiennent des conseils et des instructions permettant de savoir quel protocole choisir, de le configurer et de définir les propriétés de réglage afférentes.</span><span class="sxs-lookup"><span data-stu-id="8dee9-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="8dee9-106">WCF comprend des transports supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8dee9-106">WCF includes additional transports.</span></span> <span data-ttu-id="8dee9-107">Pour plus d’informations sur le transport Message Queuing (également appelé MSMQ), consultez [files d’attente et sessions fiables](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="8dee9-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="8dee9-108">Pour plus d’informations sur le transport d’égal à égal, consultez [mise en réseau pair à pair](peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="8dee9-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dee9-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8dee9-109">In This Section</span></span>  

 [<span data-ttu-id="8dee9-110">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="8dee9-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="8dee9-111">Présente les trois transports principaux et aborde les différents points à prendre en considération lors de leur sélection.</span><span class="sxs-lookup"><span data-stu-id="8dee9-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="8dee9-112">Sélection d'un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="8dee9-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="8dee9-113">Aborde les facteurs à prendre en considération lors de la sélection d’un élément de liaison d’encodage de message.</span><span class="sxs-lookup"><span data-stu-id="8dee9-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="8dee9-114">Transfert des messages par diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="8dee9-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="8dee9-115">Contient des instructions permettant de configurer la couche de transport pour une diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="8dee9-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="8dee9-116">Configuration de HTTP et HTTPS</span><span class="sxs-lookup"><span data-stu-id="8dee9-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="8dee9-117">Contient des instructions permettant de configurer les éléments de liaison de transport HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8dee9-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="8dee9-118">Procédure : remplacer la réservation d’URL WCF par une réservation restreinte</span><span class="sxs-lookup"><span data-stu-id="8dee9-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="8dee9-119">Décrit comment utiliser des réservations restreintes WCFURL.</span><span class="sxs-lookup"><span data-stu-id="8dee9-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="8dee9-120">Quotas de transport</span><span class="sxs-lookup"><span data-stu-id="8dee9-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="8dee9-121">Aborde les points à prendre en considération lors de la définition de quotas pour la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="8dee9-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="8dee9-122">Utilisation des NAT et des pare-feu</span><span class="sxs-lookup"><span data-stu-id="8dee9-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="8dee9-123">Contient des instructions permettant de configurer la couche de transport lorsque les messages envoyés ou reçus rencontrent un pare-feu ou lorsqu'un traducteur d'adresses réseau (NAT) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8dee9-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="8dee9-124">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="8dee9-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="8dee9-125">Décrit comment utiliser le composant de partage de port Net. TCP de WCF.</span><span class="sxs-lookup"><span data-stu-id="8dee9-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8dee9-126">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="8dee9-126">Reference</span></span>  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="8dee9-127">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="8dee9-127">Related Sections</span></span>  

 [<span data-ttu-id="8dee9-128">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8dee9-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="8dee9-129">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="8dee9-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
