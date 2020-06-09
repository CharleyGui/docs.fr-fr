---
title: 'Transport : UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 44e47dd2d291ffc27d1777a04b645d57984919cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591434"
---
# <a name="transport-udp"></a><span data-ttu-id="927da-102">Transport : UDP</span><span class="sxs-lookup"><span data-stu-id="927da-102">Transport: UDP</span></span>
<span data-ttu-id="927da-103">L’exemple de transport UDP montre comment implémenter la monodiffusion et la multidiffusion UDP comme un transport Windows Communication Foundation (WCF) personnalisé.</span><span class="sxs-lookup"><span data-stu-id="927da-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="927da-104">L’exemple décrit la procédure recommandée pour créer un transport personnalisé dans WCF, en utilisant l’infrastructure de canal et les meilleures pratiques WCF suivantes.</span><span class="sxs-lookup"><span data-stu-id="927da-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="927da-105">Les étapes de la création d'un transport personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="927da-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="927da-106">Déterminez lequel des [modèles d’échange de messages](#MessageExchangePatterns) de canal (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) que votre ChannelFactory et ChannelListener prendra en charge.</span><span class="sxs-lookup"><span data-stu-id="927da-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="927da-107">Déterminez ensuite si vous prendrez en charge les variantes de session de ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="927da-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="927da-108">Créez une fabrication et un écouteur de canal qui prennent en charge votre modèle d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="927da-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="927da-109">Assurez-vous que les exceptions spécifiques au réseau sont normalisées selon la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="927da-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="927da-110">Ajoutez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément qui ajoute le transport personnalisé à une pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="927da-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="927da-111">Pour plus d’informations, consultez [Ajout d’un élément de liaison](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="927da-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="927da-112">Ajoutez une section d’extension d’élément de liaison afin d’exposer le nouvel élément de liaison au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="927da-113">Ajoutez des extensions de métadonnées pour communiquer des fonctionnalités à d'autres points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="927da-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="927da-114">Ajoutez une liaison qui préconfigure une pile d’éléments de liaison d’après un profil bien défini.</span><span class="sxs-lookup"><span data-stu-id="927da-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="927da-115">Pour plus d’informations, consultez [Ajout d’une liaison standard](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="927da-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="927da-116">Ajoutez une section de liaison ainsi qu'un élément de configuration de liaison afin d'exposer la liaison au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="927da-117">Pour plus d’informations, consultez Ajout de la [prise en charge](#AddingConfigurationSupport)de la configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="927da-118">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="927da-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="927da-119">La première étape de l’écriture d’un transport personnalisé consiste à déterminer les MEP (Message Exchange Pattern, modèle d’échange de messages) requis pour le transport.</span><span class="sxs-lookup"><span data-stu-id="927da-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="927da-120">Trois MEP sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="927da-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="927da-121">Datagramme (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="927da-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="927da-122">Lorsque vous utilisez un MEP datagramme, un client envoie un message en utilisant un échange de type « déclenché et oublié » (fire and forget).</span><span class="sxs-lookup"><span data-stu-id="927da-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="927da-123">Un échange de ce type requiert une confirmation hors bande de la réussite de la remise.</span><span class="sxs-lookup"><span data-stu-id="927da-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="927da-124">Le message peut être perdu lors de la transmission et ne jamais atteindre le service.</span><span class="sxs-lookup"><span data-stu-id="927da-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="927da-125">Si l'opération d'envoi s'exécute correctement au niveau du client, cela ne garantit pas que le point de terminaison distant a effectivement reçu le message.</span><span class="sxs-lookup"><span data-stu-id="927da-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="927da-126">Le datagramme est un bloc de construction de messagerie fondamental. Vous pouvez en effet définir vos propres protocoles au-dessus de ce bloc, notamment des protocoles fiables et sécurisés.</span><span class="sxs-lookup"><span data-stu-id="927da-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="927da-127">Les canaux de datagramme du client implémentent l'interface <xref:System.ServiceModel.Channels.IOutputChannel> et ceux du service implémentent l'interface <xref:System.ServiceModel.Channels.IInputChannel>.</span><span class="sxs-lookup"><span data-stu-id="927da-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="927da-128">Demande-réponse (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="927da-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="927da-129">Dans ce MEP, un message est envoyé et une réponse est reçue.</span><span class="sxs-lookup"><span data-stu-id="927da-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="927da-130">Ce modèle se compose de paires demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="927da-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="927da-131">Parmi les exemples d'appels demande-réponse figurent notamment les appels de procédure distante (RPC) et les demandes GET de navigateur.</span><span class="sxs-lookup"><span data-stu-id="927da-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="927da-132">Ce modèle est également connu sous le nom de mode semi-duplex.</span><span class="sxs-lookup"><span data-stu-id="927da-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="927da-133">Dans ce MEP, les canaux du client implémentent <xref:System.ServiceModel.Channels.IRequestChannel> et ceux du service implémentent <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="927da-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="927da-134">Duplex (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="927da-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="927da-135">Le MEP duplex permet à un nombre aléatoire de messages d'être envoyés par un client et d'être reçus dans un ordre indifférencié.</span><span class="sxs-lookup"><span data-stu-id="927da-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="927da-136">Le MEP duplex est similaire à une conversation téléphonique, où chaque mot prononcé correspond à un message.</span><span class="sxs-lookup"><span data-stu-id="927da-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="927da-137">Les deux côtés pouvant envoyer et recevoir des messages dans ce MEP, l'interface implémentée par les canaux du client et du service est <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="927da-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="927da-138">Chacun de ces MEP peut également prendre en charge des sessions.</span><span class="sxs-lookup"><span data-stu-id="927da-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="927da-139">Les fonctionnalités fournies par un canal de session permettent de corréler tous les messages envoyés et reçus sur un canal.</span><span class="sxs-lookup"><span data-stu-id="927da-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="927da-140">Le modèle demande-réponse correspond à une session autonome à deux messages, la demande et la réponse étant corrélées.</span><span class="sxs-lookup"><span data-stu-id="927da-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="927da-141">En revanche, le modèle demande-réponse qui prend en charge les sessions implique que toutes les paires demande/réponse sur ce canal soient corrélées les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="927da-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="927da-142">Six MEP sont donc disponibles au total : datagramme, demande-réponse, duplex, datagramme avec sessions, demande-réponse avec sessions et duplex avec sessions.</span><span class="sxs-lookup"><span data-stu-id="927da-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="927da-143">Concernant le transport UDP, le seul MEP pris en charge est datagramme, le protocole UDP étant de part nature un protocole de type « déclenché et oublié ».</span><span class="sxs-lookup"><span data-stu-id="927da-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="927da-144">ICommunicationObject et cycle de vie des objets WCF</span><span class="sxs-lookup"><span data-stu-id="927da-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="927da-145">WCF possède un ordinateur d’État commun qui est utilisé pour gérer le cycle de vie d’objets tels que <xref:System.ServiceModel.Channels.IChannel> , <xref:System.ServiceModel.Channels.IChannelFactory> , et <xref:System.ServiceModel.Channels.IChannelListener> qui sont utilisés pour la communication.</span><span class="sxs-lookup"><span data-stu-id="927da-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="927da-146">Ces objets de communication peuvent avoir cinq états différents.</span><span class="sxs-lookup"><span data-stu-id="927da-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="927da-147">Ces états sont représentés par l'énumération <xref:System.ServiceModel.CommunicationState> et sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="927da-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="927da-148">Created : état d'un <xref:System.ServiceModel.ICommunicationObject> lorsqu'il est instancié pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="927da-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="927da-149">Aucune entrée/sortie (E/S) ne se produit dans cet état.</span><span class="sxs-lookup"><span data-stu-id="927da-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="927da-150">Opening : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Open%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="927da-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="927da-151">À ce stade, les propriétés sont rendues immuables, et les entrées/sorties peuvent commencer.</span><span class="sxs-lookup"><span data-stu-id="927da-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="927da-152">Cette transition est uniquement valide à partir de l'état Created.</span><span class="sxs-lookup"><span data-stu-id="927da-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="927da-153">Opened : les objets passent à cet état lorsque le processus d'ouverture est terminé.</span><span class="sxs-lookup"><span data-stu-id="927da-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="927da-154">Cette transition est uniquement valide à partir de l'état Opening.</span><span class="sxs-lookup"><span data-stu-id="927da-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="927da-155">À ce stade, l'objet est totalement utilisable pour le transfert.</span><span class="sxs-lookup"><span data-stu-id="927da-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="927da-156">Closing : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Close%2A> est appelé pour un arrêt approprié.</span><span class="sxs-lookup"><span data-stu-id="927da-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="927da-157">Cette transition est uniquement valide à partir de l'état Opened.</span><span class="sxs-lookup"><span data-stu-id="927da-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="927da-158">Closed : dans cet état, les objets ne sont plus utilisables.</span><span class="sxs-lookup"><span data-stu-id="927da-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="927da-159">En général, la configuration est encore accessible pour l'inspection, mais aucune communication ne peut se produire.</span><span class="sxs-lookup"><span data-stu-id="927da-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="927da-160">Cet état est équivalent à la suppression des objets.</span><span class="sxs-lookup"><span data-stu-id="927da-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="927da-161">Faulted : dans cet état, les objets sont accessibles pour l'inspection, mais e sont plus utilisables.</span><span class="sxs-lookup"><span data-stu-id="927da-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="927da-162">Lorsqu'une erreur non récupérable se produit, l'objet passe à cet état.</span><span class="sxs-lookup"><span data-stu-id="927da-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="927da-163">La seule transition valide à partir de cet État est à l' `Closed` État.</span><span class="sxs-lookup"><span data-stu-id="927da-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="927da-164">Des événements se déclenchent pour chaque transition d'état.</span><span class="sxs-lookup"><span data-stu-id="927da-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="927da-165">La méthode <xref:System.ServiceModel.ICommunicationObject.Abort%2A> peut être appelée à tout moment et provoquer la transition immédiate de l'objet de son état actuel à l'état Closed.</span><span class="sxs-lookup"><span data-stu-id="927da-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="927da-166">L'appel de <xref:System.ServiceModel.ICommunicationObject.Abort%2A> termine toute tâche inachevée.</span><span class="sxs-lookup"><span data-stu-id="927da-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="927da-167">Fabrication et écouteur de canal</span><span class="sxs-lookup"><span data-stu-id="927da-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="927da-168">L'étape suivante de l'écriture d'un transport personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service.</span><span class="sxs-lookup"><span data-stu-id="927da-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="927da-169">La couche de canal utilise un modèle de fabrication pour construire des canaux.</span><span class="sxs-lookup"><span data-stu-id="927da-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="927da-170">WCF fournit des applications auxiliaires de classe de base pour ce processus.</span><span class="sxs-lookup"><span data-stu-id="927da-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="927da-171">La classe <xref:System.ServiceModel.Channels.CommunicationObject> implémente <xref:System.ServiceModel.ICommunicationObject> et applique la machine d'état précédemment décrite à l'étape 2.</span><span class="sxs-lookup"><span data-stu-id="927da-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="927da-172">La <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implémente <xref:System.ServiceModel.Channels.CommunicationObject> et fournit une classe de base unifiée pour <xref:System.ServiceModel.Channels.ChannelFactoryBase> et <xref:System.ServiceModel.Channels.ChannelListenerBase> .</span><span class="sxs-lookup"><span data-stu-id="927da-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="927da-173">La classe <xref:System.ServiceModel.Channels.ChannelManagerBase> fonctionne avec <xref:System.ServiceModel.Channels.ChannelBase>, qui est une classe de base implémentant <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="927da-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="927da-174">La <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implémente <xref:System.ServiceModel.Channels.ChannelManagerBase> et <xref:System.ServiceModel.Channels.IChannelFactory> consolide les `CreateChannel` surcharges dans une `OnCreateChannel` méthode abstraite.</span><span class="sxs-lookup"><span data-stu-id="927da-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="927da-175">La <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implémente <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="927da-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="927da-176">Elle se charge de la gestion d'état de base.</span><span class="sxs-lookup"><span data-stu-id="927da-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="927da-177">Dans cet exemple, l'implémentation de la fabrication est contenue dans UdpChannelFactory.cs et l'implémentation de l'écouteur est contenue dans UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="927da-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="927da-178">Les implémentations <xref:System.ServiceModel.Channels.IChannel> sont contenues dans UdpOutputChannel.cs et UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="927da-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="927da-179">Fabrication de canal UDP</span><span class="sxs-lookup"><span data-stu-id="927da-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="927da-180">`UdpChannelFactory` dérive de <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="927da-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="927da-181">L'exemple substitue <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pour fournir un accès à la version du message de l'encodeur de message.</span><span class="sxs-lookup"><span data-stu-id="927da-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="927da-182">L'exemple substitue également <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> afin de nous permettre de détruire notre instance de <xref:System.ServiceModel.Channels.BufferManager> lors des transitions de la machine d'état.</span><span class="sxs-lookup"><span data-stu-id="927da-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="927da-183">Canal de sortie UDP</span><span class="sxs-lookup"><span data-stu-id="927da-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="927da-184">`UdpOutputChannel` implémente <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="927da-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="927da-185">Le constructeur valide les arguments et construit un objet <xref:System.Net.EndPoint> de destination reposant sur le <xref:System.ServiceModel.EndpointAddress> qui est passé.</span><span class="sxs-lookup"><span data-stu-id="927da-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="927da-186">Le canal peut être fermé de façon appropriée ou incorrecte.</span><span class="sxs-lookup"><span data-stu-id="927da-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="927da-187">Si le canal est fermé de façon normale, le socket est fermé et un appel à la méthode `OnClose` de la classe de base est réalisé.</span><span class="sxs-lookup"><span data-stu-id="927da-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="927da-188">Si une exception est alors levée, l'infrastructure appelle `Abort` pour veiller à ce que le canal soit nettoyé.</span><span class="sxs-lookup"><span data-stu-id="927da-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="927da-189">Nous implémentons ensuite `Send()` et `BeginSend()` / `EndSend()` .</span><span class="sxs-lookup"><span data-stu-id="927da-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="927da-190">Deux phases peuvent alors être distinguées.</span><span class="sxs-lookup"><span data-stu-id="927da-190">This breaks down into two main sections.</span></span> <span data-ttu-id="927da-191">Tout d'abord, la sérialisation du message dans un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="927da-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="927da-192">Puis, l'envoi des données résultantes sur le câble.</span><span class="sxs-lookup"><span data-stu-id="927da-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="927da-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="927da-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="927da-194">Le `UdpChannelListener` que l’exemple implémente dérive de la <xref:System.ServiceModel.Channels.ChannelListenerBase> classe.</span><span class="sxs-lookup"><span data-stu-id="927da-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="927da-195">Il utilise un socket UDP unique pour recevoir des datagrammes.</span><span class="sxs-lookup"><span data-stu-id="927da-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="927da-196">La méthode `OnOpen` reçoit des données à l'aide du socket UDP dans une boucle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="927da-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="927da-197">Les données sont ensuite converties en messages à l'aide de l'infrastructure d'encodage de message.</span><span class="sxs-lookup"><span data-stu-id="927da-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="927da-198">Étant donné que le même canal de datagramme représente des messages qui arrivent de plusieurs sources, l'`UdpChannelListener` est un écouteur Singleton.</span><span class="sxs-lookup"><span data-stu-id="927da-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="927da-199">Il y a, au plus, un actif <xref:System.ServiceModel.Channels.IChannel> associé à cet écouteur à la fois.</span><span class="sxs-lookup"><span data-stu-id="927da-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="927da-200">L'exemple en génère un autre uniquement si un canal retourné par la méthode `AcceptChannel` est disposé par la suite.</span><span class="sxs-lookup"><span data-stu-id="927da-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="927da-201">Lorsqu'un message est reçu, il est mis en file d'attente dans ce canal singleton.</span><span class="sxs-lookup"><span data-stu-id="927da-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="927da-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="927da-202">UdpInputChannel</span></span>  
 <span data-ttu-id="927da-203">La `UdpInputChannel` classe implémente `IInputChannel` .</span><span class="sxs-lookup"><span data-stu-id="927da-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="927da-204">Elle se compose d'une file d'attente de messages entrants remplie par le socket de `UdpChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="927da-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="927da-205">Ces messages sont extraits de la file d'attente par la méthode `IInputChannel.Receive`.</span><span class="sxs-lookup"><span data-stu-id="927da-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="927da-206">Ajout d'un élément de liaison</span><span class="sxs-lookup"><span data-stu-id="927da-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="927da-207">Maintenant que les fabrications de canaux sont construites, nous devons les exposer à l’exécution de ServiceModel via une liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="927da-208">Une liaison est une collection d’éléments de liaison qui représente la pile de communication associée à une adresse de service.</span><span class="sxs-lookup"><span data-stu-id="927da-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="927da-209">Chaque élément de la pile est représenté par un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="927da-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="927da-210">Dans notre exemple, l'élément de liaison est `UdpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="927da-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="927da-211">Il substitue les méthodes suivantes pour générer les fabrications associées à notre liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="927da-212">Il contient également des membres permettant de cloner `BindingElement` et de retourner notre schéma (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="927da-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="927da-213">Ajout de la prise en charge des métadonnées pour un élément de liaison de transport</span><span class="sxs-lookup"><span data-stu-id="927da-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="927da-214">Pour intégrer notre transport dans le système de métadonnées, nous devons prendre à la fois en charge l'importation et l'exportation de stratégie.</span><span class="sxs-lookup"><span data-stu-id="927da-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="927da-215">Cela nous permet de générer des clients de notre liaison via l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="927da-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="927da-216">Ajout de la prise en charge WSDL</span><span class="sxs-lookup"><span data-stu-id="927da-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="927da-217">L’élément de liaison de transport d’une liaison est chargé d’exporter et d’importer les informations d’adressage dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="927da-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="927da-218">Lors de l'utilisation d'une liaison SOAP, l'élément de liaison de transport doit également exporter un URI de transport correct dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="927da-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="927da-219">Exportation WSDL</span><span class="sxs-lookup"><span data-stu-id="927da-219">WSDL Export</span></span>  
 <span data-ttu-id="927da-220">Pour exporter des informations d'adressage, `UdpTransportBindingElement` implémente l'interface `IWsdlExportExtension`.</span><span class="sxs-lookup"><span data-stu-id="927da-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="927da-221">La méthode `ExportEndpoint` ajoute les informations d'adressage correctes au port WSDL.</span><span class="sxs-lookup"><span data-stu-id="927da-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="927da-222">L’implémentation `UdpTransportBindingElement` de la méthode `ExportEndpoint` exporte également un URI de transport lorsque le point de terminaison utilise une liaison SOAP.</span><span class="sxs-lookup"><span data-stu-id="927da-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="927da-223">Importation WSDL</span><span class="sxs-lookup"><span data-stu-id="927da-223">WSDL Import</span></span>  
 <span data-ttu-id="927da-224">Pour étendre le système d'importation WSDL afin de gérer l'importation des adresses, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="927da-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="927da-225">Lorsque vous exécutez Svcutil.exe, deux méthodes permettent de faire en sorte que Svcutil.exe charge les extensions d’importation WSDL :</span><span class="sxs-lookup"><span data-stu-id="927da-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="927da-226">Pointez Svcutil. exe vers notre fichier de configuration à l’aide du en utilisant/svcutilConfig : \<file> .</span><span class="sxs-lookup"><span data-stu-id="927da-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="927da-227">Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="927da-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="927da-228">Le type `UdpBindingElementImporter` implémente l'interface `IWsdlImportExtension`.</span><span class="sxs-lookup"><span data-stu-id="927da-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="927da-229">La méthode `ImportEndpoint` importe l'adresse à partir du port WSDL.</span><span class="sxs-lookup"><span data-stu-id="927da-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="927da-230">Ajout de la prise en charge de la stratégie</span><span class="sxs-lookup"><span data-stu-id="927da-230">Adding Policy Support</span></span>  
 <span data-ttu-id="927da-231">L’élément de liaison personnalisé peut exporter des assertions de stratégie dans la liaison WSDL d’un point de terminaison de service pour exprimer les fonctionnalités de cet élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="927da-232">Exportation de stratégie</span><span class="sxs-lookup"><span data-stu-id="927da-232">Policy Export</span></span>  
 <span data-ttu-id="927da-233">Le `UdpTransportBindingElement` type implémente `IPolicyExportExtension` pour ajouter la prise en charge de l’exportation de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="927da-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="927da-234">En conséquence, `System.ServiceModel.MetadataExporter` inclut `UdpTransportBindingElement` dans la génération de stratégie des liaisons qui l’incluent.</span><span class="sxs-lookup"><span data-stu-id="927da-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="927da-235">Dans `IPolicyExportExtension.ExportPolicy`, nous ajoutons une assertion pour UDP et une autre si nous sommes en mode multicast.</span><span class="sxs-lookup"><span data-stu-id="927da-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="927da-236">Cela est dû au fait que le mode multicast affecte la manière dont la pile est construite, et doit donc être coordonné entre les deux côtés.</span><span class="sxs-lookup"><span data-stu-id="927da-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="927da-237">Les éléments de liaison de transport personnalisés étant chargés de gérer l’adressage, l’implémentation `IPolicyExportExtension` sur `UdpTransportBindingElement` doit également gérer l’exportation des assertions de stratégie WS-Addressing appropriées pour indiquer la version de WS-Addressing utilisée.</span><span class="sxs-lookup"><span data-stu-id="927da-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="927da-238">Importation de stratégie</span><span class="sxs-lookup"><span data-stu-id="927da-238">Policy Import</span></span>  
 <span data-ttu-id="927da-239">Pour étendre le système d'importation de stratégie, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="927da-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="927da-240">Puis nous implémentons `IPolicyImporterExtension` à partir de la classe enregistrée (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="927da-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="927da-241">Dans `ImportPolicy()`, nous examinons les assertions dans notre espace de noms, puis traitons celles permettant de générer le transport et vérifions s'il est multicast.</span><span class="sxs-lookup"><span data-stu-id="927da-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="927da-242">Nous devons également supprimer les assertions que nous gérons de la liste des assertions de liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="927da-243">Une fois encore, il existe deux méthodes d'intégration possibles lorsque vous exécutez Svcutil.exe :</span><span class="sxs-lookup"><span data-stu-id="927da-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="927da-244">Pointez Svcutil. exe vers notre fichier de configuration à l’aide du en utilisant/svcutilConfig : \<file> .</span><span class="sxs-lookup"><span data-stu-id="927da-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="927da-245">Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="927da-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="927da-246">Ajout d’une liaison standard</span><span class="sxs-lookup"><span data-stu-id="927da-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="927da-247">Notre élément de liaison peut être utilisé des deux façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="927da-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="927da-248">Via une liaison personnalisée : une liaison personnalisée permet à l’utilisateur de créer sa propre la liaison en fonction d’un ensemble arbitraire d’éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="927da-249">En utilisant une liaison fournie par le système qui inclut notre élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="927da-250">WCF fournit un certain nombre de ces liaisons définies par le système, telles que `BasicHttpBinding` , `NetTcpBinding` et `WsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="927da-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="927da-251">Chacune de ces liaisons est associée à un profil bien défini.</span><span class="sxs-lookup"><span data-stu-id="927da-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="927da-252">L'exemple implémente la liaison de profil dans `SampleProfileUdpBinding`, lequel dérive de <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="927da-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="927da-253">`SampleProfileUdpBinding` contient jusqu'à quatre éléments de liaison : `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement` et `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="927da-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="927da-254">Ajout d'un importateur de liaison standard personnalisé</span><span class="sxs-lookup"><span data-stu-id="927da-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="927da-255">Par défaut, Svcutil.exe et le type `WsdlImporter` reconnaissent et importent les liaisons définies par le système.</span><span class="sxs-lookup"><span data-stu-id="927da-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="927da-256">Sinon, la liaison est importée en tant qu'instance `CustomBinding`.</span><span class="sxs-lookup"><span data-stu-id="927da-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="927da-257">Pour permettre à Svcutil.exe et `WsdlImporter` d’importer `SampleProfileUdpBinding`, `UdpBindingElementImporter` agit également comme un importateur de liaison standard personnalisé.</span><span class="sxs-lookup"><span data-stu-id="927da-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="927da-258">Un importateur de liaison standard personnalisé implémente la méthode `ImportEndpoint` sur l'interface `IWsdlImportExtension` pour examiner l'instance `CustomBinding` importée à partir des métadonnées afin de vérifier si elle peut avoir été générée par une liaison standard spécifique.</span><span class="sxs-lookup"><span data-stu-id="927da-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="927da-259">En général, l’implémentation d’un importateur de liaison standard personnalisé implique la vérification des propriétés des éléments de liaison importés afin de s’assurer que seules les propriétés pouvant avoir été définies par la liaison standard ont été modifiées et que toutes les autres ont été définies à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="927da-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="927da-260">L’une des stratégies de base permettant d’implémenter un importateur de liaison standard consiste à créer une instance de la liaison standard, à propager les propriétés des éléments de liaison vers l’instance de liaison standard que la liaison standard prend en charge, et à comparer les éléments de liaison de la liaison standard avec les éléments de liaison importés.</span><span class="sxs-lookup"><span data-stu-id="927da-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="927da-261">Ajout de la prise en charge de la configuration</span><span class="sxs-lookup"><span data-stu-id="927da-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="927da-262">Pour exposer notre transport via la configuration, nous devons implémenter deux sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="927da-263">La première est `BindingElementExtensionElement` pour `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="927da-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="927da-264">C'est de cette façon que les implémentations `CustomBinding` référencent notre élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="927da-265">La deuxième est `Configuration` pour `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="927da-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="927da-266">Élément d’extension de l’élément de liaison</span><span class="sxs-lookup"><span data-stu-id="927da-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="927da-267">La section `UdpTransportElement` est un `BindingElementExtensionElement` qui expose `UdpTransportBindingElement` au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="927da-268">Avec quelques substitutions de base, nous définissons le nom de notre section de configuration, le type de notre élément de liaison et la méthode utilisée pour le créer.</span><span class="sxs-lookup"><span data-stu-id="927da-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="927da-269">Nous pouvons ensuite enregistrer notre section d’extension dans un fichier de configuration, tel qu’indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="927da-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="927da-270">L'extension peut être référencée à partir des liaisons personnalisées pour utiliser UDP comme transport.</span><span class="sxs-lookup"><span data-stu-id="927da-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="927da-271">Section de liaison</span><span class="sxs-lookup"><span data-stu-id="927da-271">Binding Section</span></span>  
 <span data-ttu-id="927da-272">La section `SampleProfileUdpBindingCollectionElement` est un `StandardBindingCollectionElement` qui expose `SampleProfileUdpBinding` au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="927da-273">Le bloc de l'implémentation est délégué à `SampleProfileUdpBindingConfigurationElement`, qui dérive de `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="927da-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="927da-274">`SampleProfileUdpBindingConfigurationElement`A des propriétés qui correspondent aux propriétés de `SampleProfileUdpBinding` et aux fonctions à mapper à partir de la `ConfigurationElement` liaison.</span><span class="sxs-lookup"><span data-stu-id="927da-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="927da-275">Enfin, nous substituons `OnApplyConfiguration` dans notre `SampleProfileUdpBinding`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="927da-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="927da-276">Pour enregistrer ce gestionnaire avec le système de configuration, nous ajoutons la section suivante au fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="927da-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="927da-277">Il pourra ensuite être référencé à partir de la section de configuration serviceModel.</span><span class="sxs-lookup"><span data-stu-id="927da-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="927da-278">Client et service de test UDP</span><span class="sxs-lookup"><span data-stu-id="927da-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="927da-279">Le code de test permettant d'utiliser cet exemple de transport est disponible dans les répertoires UdpTestService et UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="927da-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="927da-280">Le code de service se compose de deux tests : le premier définit les liaisons et les points de terminaison à partir du code, et le deuxième le fait via la configuration.</span><span class="sxs-lookup"><span data-stu-id="927da-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="927da-281">Ces deux tests utilisent deux points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="927da-281">Both tests use two endpoints.</span></span> <span data-ttu-id="927da-282">Un point de terminaison utilise la `SampleUdpProfileBinding` avec la [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="927da-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="927da-283">L'autre utilise une liaison personnalisée avec `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="927da-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="927da-284">Cela équivaut à utiliser `SampleUdpProfileBinding` avec avec la [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="927da-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="927da-285">Ces deux tests créent un service, ajoutent  un point de terminaison pour chaque liaison, ouvrent le service, puis attendent que l'utilisateur tape ENTER avant de fermer le service.</span><span class="sxs-lookup"><span data-stu-id="927da-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="927da-286">Lorsque vous démarrez l'application de test de service, la sortie suivante doit s'afficher.</span><span class="sxs-lookup"><span data-stu-id="927da-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="927da-287">Vous pouvez ensuite exécuter l'application de test cliente sur les points de terminaison publiés.</span><span class="sxs-lookup"><span data-stu-id="927da-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="927da-288">L'application de test cliente crée un client pour chaque point de terminaison et envoie cinq messages à chacun.</span><span class="sxs-lookup"><span data-stu-id="927da-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="927da-289">Sortie sur le client :</span><span class="sxs-lookup"><span data-stu-id="927da-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="927da-290">Sortie complète sur le service :</span><span class="sxs-lookup"><span data-stu-id="927da-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="927da-291">Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, tapez ENTER sur le service, puis exécutez de nouveau le client test.</span><span class="sxs-lookup"><span data-stu-id="927da-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="927da-292">La sortie suivante doit s'afficher sur le service.</span><span class="sxs-lookup"><span data-stu-id="927da-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="927da-293">La réexécution du client génère les mêmes résultats que ceux obtenus précédemment.</span><span class="sxs-lookup"><span data-stu-id="927da-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="927da-294">Pour régénérer le code client et la configuration à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez le fichier Svcutil.exe suivant à partir du répertoire racine de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="927da-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="927da-295">Svcutil.exe ne générant pas de configuration d’extension de liaison pour `SampleProfileUdpBinding`, vous devez donc l’ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="927da-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="927da-296">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="927da-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="927da-297">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="927da-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="927da-298">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="927da-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="927da-299">Référez-vous à la section « Client et service de test UDP » développée précédemment.</span><span class="sxs-lookup"><span data-stu-id="927da-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="927da-300">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="927da-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="927da-301">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="927da-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="927da-302">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="927da-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="927da-303">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="927da-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
