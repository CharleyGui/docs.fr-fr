---
title: Services duplex
description: Découvrez comment créer un contrat de service duplex dans WCF, ce qui permet aux deux points de terminaison d’envoyer des messages entre eux via un canal créé par le client.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247349"
---
# <a name="duplex-services"></a><span data-ttu-id="c55a7-103">Services duplex</span><span class="sxs-lookup"><span data-stu-id="c55a7-103">Duplex Services</span></span>

<span data-ttu-id="c55a7-104">Un contrat de service duplex est un modèle d'échange de messages dans lequel les deux points de terminaison peuvent envoyer indépendamment des messages à l'autre.</span><span class="sxs-lookup"><span data-stu-id="c55a7-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="c55a7-105">Un service duplex peut, par conséquent, renvoyer des messages au point de terminaison client, en fournissant un comportement de type événement.</span><span class="sxs-lookup"><span data-stu-id="c55a7-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="c55a7-106">La communication duplex se produit lorsqu'un client se connecte à un service et lui fournit un canal sur lequel il peut lui renvoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="c55a7-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="c55a7-107">Notez que le comportement de type événement des services duplex ne fonctionne que dans une session.</span><span class="sxs-lookup"><span data-stu-id="c55a7-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="c55a7-108">Pour créer un contrat duplex, créez une paire d'interfaces.</span><span class="sxs-lookup"><span data-stu-id="c55a7-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="c55a7-109">La première est l'interface de contrat de service qui décrit les opérations qu'un client peut appeler.</span><span class="sxs-lookup"><span data-stu-id="c55a7-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="c55a7-110">Ce contrat de service doit spécifier un *contrat de rappel* dans la <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="c55a7-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c55a7-111">Le contrat de rappel est l'interface qui définit les opérations que le service peut appeler sur le point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="c55a7-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="c55a7-112">Un contrat duplex ne requiert pas de session, bien que les liaisons duplex fournies par le système en utilisent.</span><span class="sxs-lookup"><span data-stu-id="c55a7-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="c55a7-113">Voici un exemple de contrat duplex :</span><span class="sxs-lookup"><span data-stu-id="c55a7-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="c55a7-114">La classe `CalculatorService` implémente l'interface `ICalculatorDuplex` principale.</span><span class="sxs-lookup"><span data-stu-id="c55a7-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="c55a7-115">Le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode.PerSession> pour conserver le résultat de chaque session.</span><span class="sxs-lookup"><span data-stu-id="c55a7-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="c55a7-116">Une propriété privée appelée `Callback` accède au canal de rappel au client.</span><span class="sxs-lookup"><span data-stu-id="c55a7-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="c55a7-117">Le service utilise le rappel pour renvoyer des messages au client via l'interface de rappel, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c55a7-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="c55a7-118">Le client doit fournir une classe qui implémente l'interface de rappel du contrat duplex pour permettre la réception des messages envoyés par le service.</span><span class="sxs-lookup"><span data-stu-id="c55a7-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="c55a7-119">L'exemple de code suivant présente une classe `CallbackHandler` qui implémente l'interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="c55a7-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="c55a7-120">Le client WCF généré pour un contrat duplex requiert qu’une <xref:System.ServiceModel.InstanceContext> classe soit fournie au moment de la construction.</span><span class="sxs-lookup"><span data-stu-id="c55a7-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="c55a7-121">Cette classe <xref:System.ServiceModel.InstanceContext> est utilisée comme site pour un objet qui implémente l'interface de rappel et gère les messages renvoyés à partir du service.</span><span class="sxs-lookup"><span data-stu-id="c55a7-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="c55a7-122">Une classe <xref:System.ServiceModel.InstanceContext> est construite avec une instance de la classe `CallbackHandler`.</span><span class="sxs-lookup"><span data-stu-id="c55a7-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="c55a7-123">Cet objet gère les messages envoyés par le service au client sur l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="c55a7-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="c55a7-124">La configuration pour le service doit être installée pour fournir une liaison prenant à la fois en charge la communication de session et la communication duplex.</span><span class="sxs-lookup"><span data-stu-id="c55a7-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="c55a7-125">L'élément `wsDualHttpBinding` prend en charge la communication de session et permet la communication duplex en fournissant des connexions HTTP doubles, à raison d'une pour chaque direction.</span><span class="sxs-lookup"><span data-stu-id="c55a7-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="c55a7-126">Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de s'y connecter, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="c55a7-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c55a7-127">Les clients non duplex qui ne parviennent pas à s'authentifier à l'aide d'une conversation sécurisée lèvent en général une exception <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="c55a7-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="c55a7-128">Toutefois, si un client duplex qui utilise une conversation sécurisée ne parvient pas à s'authentifier, il reçoit à la place une exception <xref:System.TimeoutException>.</span><span class="sxs-lookup"><span data-stu-id="c55a7-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="c55a7-129">Si vous créez un client/service à l'aide de l'élément `WSHttpBinding` et que vous n'incluez pas le point de terminaison de rappel client, vous recevrez l'erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="c55a7-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="c55a7-130">L’exemple de code suivant montre comment spécifier l’adresse de point de terminaison du client par programme.</span><span class="sxs-lookup"><span data-stu-id="c55a7-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

<span data-ttu-id="c55a7-131">L'exemple de code suivant indique comment spécifier l'adresse de point de terminaison client dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c55a7-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> <span data-ttu-id="c55a7-132">Le modèle duplex ne détecte pas automatiquement quand un service ou un client ferme son canal.</span><span class="sxs-lookup"><span data-stu-id="c55a7-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="c55a7-133">Par conséquent, si un client se termine de manière inattendue, par défaut, le service n’est pas notifié, ou si un service se termine de manière inattendue, le client n’est pas notifié.</span><span class="sxs-lookup"><span data-stu-id="c55a7-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="c55a7-134">Si vous utilisez un service déconnecté, l' <xref:System.ServiceModel.CommunicationException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="c55a7-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="c55a7-135">Les clients et les services peuvent implémenter leur propre protocole pour se notifier mutuellement s'ils le souhaitent.</span><span class="sxs-lookup"><span data-stu-id="c55a7-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="c55a7-136">Pour plus d’informations sur la gestion des erreurs, consultez [gestion des erreurs WCF](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="c55a7-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c55a7-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c55a7-137">See also</span></span>

- [<span data-ttu-id="c55a7-138">Duplex</span><span class="sxs-lookup"><span data-stu-id="c55a7-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="c55a7-139">Spécification du comportement du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="c55a7-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="c55a7-140">Guide pratique pour créer et utiliser une fabrique de canaux pour créer et gérer des canaux</span><span class="sxs-lookup"><span data-stu-id="c55a7-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
