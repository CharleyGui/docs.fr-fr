---
title: Custom Message Filter
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183890"
---
# <a name="custom-message-filter"></a><span data-ttu-id="f4ad0-102">Custom Message Filter</span><span class="sxs-lookup"><span data-stu-id="f4ad0-102">Custom Message Filter</span></span>
<span data-ttu-id="f4ad0-103">Cet exemple montre comment remplacer les filtres de message que Windows Communication Foundation (WCF) utilise pour envoyer des messages aux points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4ad0-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f4ad0-105">Lorsque le premier message sur un canal arrive au niveau du serveur, ce dernier doit déterminer le point de terminaison (le cas échéant) associé à cet URI qui doit recevoir le message.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="f4ad0-106">Ce processus est contrôlé par les objets <xref:System.ServiceModel.Dispatcher.MessageFilter> joints à <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="f4ad0-107">Chaque point de terminaison d'un service a un <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> unique.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="f4ad0-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> possède à la fois <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="f4ad0-109">L'association de ces deux filtres forme le filtre de messages utilisé pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="f4ad0-110">Par défaut, le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> d'un point de terminaison correspond aux messages envoyés à une adresse qui correspond au <xref:System.ServiceModel.EndpointAddress> du point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="f4ad0-111">Par défaut, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> le point de terminaison inspecte l’action du message entrant et associe tout message à une action `IsInitiating` = `true` qui correspond à l’une des actions des opérations du contrat de fin de service (seules les actions sont prises en considération).</span><span class="sxs-lookup"><span data-stu-id="f4ad0-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="f4ad0-112">Par défaut, le filtre d'un point de terminaison correspond donc uniquement si l'en-tête To du message est le <xref:System.ServiceModel.EndpointAddress> du point de terminaison et que l'action du message correspond à l'une des actions de l'opération de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="f4ad0-113">Ces filtres peuvent être modifiés à l'aide d'un comportement.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="f4ad0-114">Dans l'exemple, le service crée un <xref:System.ServiceModel.Description.IEndpointBehavior> qui remplace <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> sur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="f4ad0-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="f4ad0-115">Deux filtres d'adresse sont définis :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="f4ad0-116">`FilteringEndpointBehavior` est rendu configurable et accepte deux variantes différentes.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="f4ad0-117">La variante 1 correspond uniquement aux adresses qui contiennent un 'e' (mais qui comportent des actions), tandis que la variante 2 correspond uniquement aux adresses sans 'e' :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="f4ad0-118">Dans le fichier de configuration, le service enregistre le nouveau comportement :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="f4ad0-119">Il crée ensuite des configurations `endpointBehavior` pour chaque variante :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="f4ad0-120">Enfin, le point de terminaison du service référence l'un des `behaviorConfigurations` :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="f4ad0-121">L'implémentation de l'application cliente est simple : elle crée deux canaux à l'URI du service (en passant cette valeur comme deuxième paramètre (`via`) à <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29>) et envoie un message unique sur chaque canal, mais utilise des adresses de point de terminaison différentes pour chacun d'entre eux.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="f4ad0-122">Par conséquent, les messages sortants provenant du client ont des désignations To différentes, et le serveur réagit en conséquence, tel qu'indiqué par la sortie du client :</span><span class="sxs-lookup"><span data-stu-id="f4ad0-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="f4ad0-123">Le passage d’une variante à une autre dans le fichier de configuration du serveur provoque la permutation du filtre et l’activation du comportement opposé sur le client (le message à `urn:e` réussit, alors que le message à `urn:a` échoue).</span><span class="sxs-lookup"><span data-stu-id="f4ad0-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f4ad0-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4ad0-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f4ad0-126">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4ad0-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4ad0-128">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f4ad0-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f4ad0-129">Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ad0-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f4ad0-130">Pour exécuter l’échantillon dans une configuration mono-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ad0-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f4ad0-131">Pour exécuter l’échantillon dans une configuration multi-machine, suivez les instructions de [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) et modifiez la ligne suivante en Client.cs.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="f4ad0-132">Remplacez localhost par le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="f4ad0-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
