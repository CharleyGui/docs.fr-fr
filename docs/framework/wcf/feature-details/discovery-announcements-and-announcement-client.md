---
title: Annonces de découverte et client d'annonce
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 74362343dc1fd5df6d1b91537f7fed5bc08f8fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968816"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="67746-102">Annonces de découverte et client d'annonce</span><span class="sxs-lookup"><span data-stu-id="67746-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="67746-103">La fonctionnalité de découverte WCF permet aux composants d’annoncer leur disponibilité.</span><span class="sxs-lookup"><span data-stu-id="67746-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="67746-104">S'il est configuré pour, un service envoie des annonces de type Hello et Bye.</span><span class="sxs-lookup"><span data-stu-id="67746-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="67746-105">Les clients ou d'autres composants peuvent écouter les messages d'annonce de ce type et agir dessus.</span><span class="sxs-lookup"><span data-stu-id="67746-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="67746-106">Cela offre une autre méthode aux clients pour être informés des services.</span><span class="sxs-lookup"><span data-stu-id="67746-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="67746-107">Les fonctionnalités d'annonce ont plusieurs utilisations, par exemple, si les services entrent dans un réseau et le quittent fréquemment, les annonces peuvent constituer une meilleure solution que de rechercher des services.</span><span class="sxs-lookup"><span data-stu-id="67746-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="67746-108">Avec cette approche, le trafic réseau est réduit et le client peut être informé de la présence ou du départ du service dès la réception des annonces.</span><span class="sxs-lookup"><span data-stu-id="67746-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="67746-109">Annonces de découverte</span><span class="sxs-lookup"><span data-stu-id="67746-109">Discovery Announcements</span></span>  
 <span data-ttu-id="67746-110">Lorsqu'un service configuré pour les annonces rejoint un réseau et devient détectable, il envoie un message de type Hello qui annonce sa disponibilité aux clients qui écoutent.</span><span class="sxs-lookup"><span data-stu-id="67746-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="67746-111">Le message contient les informations sur le service liées à la découverte, tel que son contrat, l'adresse du point de terminaison et les étendues associées.</span><span class="sxs-lookup"><span data-stu-id="67746-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="67746-112">Vous pouvez spécifier où est envoyé le message d'annonce à l'aide de la classe <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="67746-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="67746-113">Si le point de terminaison d'annonce est un objet <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, les messages de types Hello et Bye sont envoyés en mode multidiffusion de manière appropriée, ou si le point de terminaison d'annonce est en mode monodiffusion, les messages sont envoyés directement au point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="67746-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67746-114">Les annonces sont envoyées lors de l'ouverture et de la fermeture de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="67746-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="67746-115">Si ces appels ne se terminent pas correctement, le message d'annonce peut ne pas être envoyé. Par exemple si le service est défaillant, le message d'annonce de type Bye n'est pas envoyé.</span><span class="sxs-lookup"><span data-stu-id="67746-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="67746-116">Vous pouvez personnaliser les fonctionnalités d'annonce, ce qui vous permet d'envoyer des annonces quand vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="67746-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="67746-117">définit les points de terminaison <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> et <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> comme points de terminaison standard pour permettre aux services et aux clients d'envoyer facilement des annonces de type Hello et Bye.</span><span class="sxs-lookup"><span data-stu-id="67746-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="67746-118">Annonces sur le service</span><span class="sxs-lookup"><span data-stu-id="67746-118">Announcements on the Service</span></span>  
 <span data-ttu-id="67746-119">Pour configurer le service pour envoyer des annonces, ajoutez un <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> avec un point de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="67746-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="67746-120">L'exemple suivant indique comment ajouter ce comportement par programme à l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="67746-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="67746-121">Cet exemple utilise `UdpAnnouncementEndpoint`, ce qui implique que les annonces sont envoyées en mode multidiffusion à un emplacement spécifié par ce point de terminaison de standard.</span><span class="sxs-lookup"><span data-stu-id="67746-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="67746-122">Le comportement peut également être configuré dans le fichier de configuration, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="67746-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 <span data-ttu-id="67746-123">Les exemples précédents configurent un service pour envoyer automatiquement des messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="67746-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="67746-124">Vous pouvez également envoyer explicitement des messages d'annonce à l'aide de la classe <xref:System.ServiceModel.Discovery.AnnouncementClient>.</span><span class="sxs-lookup"><span data-stu-id="67746-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="67746-125">Annonces sur le client</span><span class="sxs-lookup"><span data-stu-id="67746-125">Announcements on the Client</span></span>  
 <span data-ttu-id="67746-126">Une application cliente doit héberger un service d'annonce pour répondre aux messages de type Hello et Bye et s'abonner aux événements <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> et <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived>.</span><span class="sxs-lookup"><span data-stu-id="67746-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="67746-127">L'exemple suivant montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="67746-127">The following example shows how to do this.</span></span>  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 <span data-ttu-id="67746-128">Lorsqu'un message de type Hello ou Bye est reçu, vous pouvez accéder aux métadonnées de découverte du point de terminaison via <xref:System.ServiceModel.Discovery.AnnouncementEventArgs>, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="67746-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
