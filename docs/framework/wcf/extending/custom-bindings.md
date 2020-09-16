---
title: Liaisons personnalisées
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 062aba26227fedeea3e5f462ebf5d55cf0cba56c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539995"
---
# <a name="custom-bindings"></a><span data-ttu-id="46c50-102">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="46c50-102">Custom Bindings</span></span>

<span data-ttu-id="46c50-103">Vous pouvez utiliser la classe <xref:System.ServiceModel.Channels.CustomBinding> lorsque l’une des liaisons fournies par le système ne répond pas aux spécifications de votre service.</span><span class="sxs-lookup"><span data-stu-id="46c50-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="46c50-104">Toutes les liaisons sont construites à partir d’un ensemble ordonné d’éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="46c50-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="46c50-105">Les liaisons personnalisées peuvent être construites à partir d’un jeu d’éléments de liaison fournis par le système ou peuvent inclure des éléments de liaison personnalisés définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46c50-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="46c50-106">Vous pouvez utiliser des éléments de liaison personnalisés pour activer, par exemple, l’utilisation de nouveaux transports ou encodeurs au niveau d’un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="46c50-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="46c50-107">Pour obtenir des exemples fonctionnels, consultez [exemples de liaisons personnalisées](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="46c50-107">For working examples, see [Custom Binding Samples](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="46c50-108">Pour plus d’informations, consultez [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="46c50-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="46c50-109">Construction d’une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="46c50-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="46c50-110">Une liaison personnalisée est construite à l’aide du constructeur <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> à partir d’éléments de liaison « empilés » dans un ordre spécifique :</span><span class="sxs-lookup"><span data-stu-id="46c50-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="46c50-111">Au sommet de cette pile se trouve une classe <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> facultative qui autorise les transactions de flux.</span><span class="sxs-lookup"><span data-stu-id="46c50-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="46c50-112">L'élément suivant est une classe <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> facultative qui fournit une session et des mécanismes de classement tel que défini dans la spécification WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="46c50-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="46c50-113">Une session peut traverser les intermédiaires SOAP et de transport.</span><span class="sxs-lookup"><span data-stu-id="46c50-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="46c50-114">L’élément suivant est une classe <xref:System.ServiceModel.Channels.SecurityBindingElement> facultative qui fournit des fonctionnalités de sécurité telles que l’autorisation, l’authentification, la protection et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="46c50-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="46c50-115">Vous trouverez ensuite une classe <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> facultative qui permet de disposer d'une communication en duplex bidirectionnelle avec un protocole de transport qui ne prend pas en charge la communication en duplex en mode natif, comme HTTP.</span><span class="sxs-lookup"><span data-stu-id="46c50-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="46c50-116">Vous trouverez ensuite une classe <xref:System.ServiceModel.Channels.OneWayBindingElement> facultative qui fournit une communication unidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="46c50-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="46c50-117">Puis, vous trouverez un élément de liaison de sécurité de flux de données facultatif qui peut être l’un des éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="46c50-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="46c50-118">L’élément suivant est un message obligatoire qui encode l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="46c50-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="46c50-119">Vous pouvez utiliser votre propre encodeur de message ou l’une des trois liaisons d’encodage de message :</span><span class="sxs-lookup"><span data-stu-id="46c50-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="46c50-120">Au bas de la pile se trouve un élément de transport obligatoire.</span><span class="sxs-lookup"><span data-stu-id="46c50-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="46c50-121">Vous pouvez utiliser votre propre transport ou l’un des éléments de liaison de transport suivants Windows Communication Foundation (WCF) fournit :</span><span class="sxs-lookup"><span data-stu-id="46c50-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="46c50-122">Le tableau suivant récapitule les options de chaque couche.</span><span class="sxs-lookup"><span data-stu-id="46c50-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="46c50-123">Couche</span><span class="sxs-lookup"><span data-stu-id="46c50-123">Layer</span></span>|<span data-ttu-id="46c50-124">Options</span><span class="sxs-lookup"><span data-stu-id="46c50-124">Options</span></span>|<span data-ttu-id="46c50-125">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="46c50-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="46c50-126">Transactions</span><span class="sxs-lookup"><span data-stu-id="46c50-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="46c50-127">Non</span><span class="sxs-lookup"><span data-stu-id="46c50-127">No</span></span>|
|<span data-ttu-id="46c50-128">Fiabilité</span><span class="sxs-lookup"><span data-stu-id="46c50-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="46c50-129">Non</span><span class="sxs-lookup"><span data-stu-id="46c50-129">No</span></span>|
|<span data-ttu-id="46c50-130">Sécurité</span><span class="sxs-lookup"><span data-stu-id="46c50-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="46c50-131">Non</span><span class="sxs-lookup"><span data-stu-id="46c50-131">No</span></span>|
|<span data-ttu-id="46c50-132">Encodage</span><span class="sxs-lookup"><span data-stu-id="46c50-132">Encoding</span></span>|<span data-ttu-id="46c50-133">Texte, binaire, MTOM (Message Transmission Optimization Mechanism), personnalisé</span><span class="sxs-lookup"><span data-stu-id="46c50-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="46c50-134">Oui</span><span class="sxs-lookup"><span data-stu-id="46c50-134">Yes</span></span>|
|<span data-ttu-id="46c50-135">Transport</span><span class="sxs-lookup"><span data-stu-id="46c50-135">Transport</span></span>|<span data-ttu-id="46c50-136">TCP, HTTP, HTTPS, canaux nommés (également appelés IPC), P2P (Peer-to-Peer), Message Queuing (également appelé MSMQ), Custom</span><span class="sxs-lookup"><span data-stu-id="46c50-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="46c50-137">Oui</span><span class="sxs-lookup"><span data-stu-id="46c50-137">Yes</span></span>|

<span data-ttu-id="46c50-138">De plus, vous pouvez définir vos propres éléments de liaison et les insérer entre chacune des couches définies précédentes.</span><span class="sxs-lookup"><span data-stu-id="46c50-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="46c50-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46c50-139">See also</span></span>

- [<span data-ttu-id="46c50-140">Vue d'ensemble de la création de points de terminaison</span><span class="sxs-lookup"><span data-stu-id="46c50-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="46c50-141">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="46c50-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="46c50-142">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="46c50-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="46c50-143">Procédure : personnaliser une liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="46c50-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="46c50-144">Liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="46c50-144">Custom Binding</span></span>](../samples/custom-binding.md)
