---
title: Exemple Announcements
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: c3824fb0dc7ab4169c309d1a5154127d6bc3b78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746998"
---
# <a name="announcements-sample"></a><span data-ttu-id="bd0f6-102">Exemple Announcements</span><span class="sxs-lookup"><span data-stu-id="bd0f6-102">Announcements Sample</span></span>

<span data-ttu-id="bd0f6-103">Cet exemple montre comment utiliser les fonctionnalités d’annonce de la découverte.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="bd0f6-104">Les annonces permettent aux services d'envoyer des messages d'annonce qui contiennent des métadonnées relatives au service.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="bd0f6-105">Par défaut, une annonce de type Hello est envoyée lorsque le service démarre et une annonce de type Bye est envoyée lorsque le service s'arrête.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="bd0f6-106">Ces annonces peuvent être envoyées en mode multidiffusion ou de point à point.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="bd0f6-107">Cet exemple se compose de deux projets : service et client.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="bd0f6-108">Service</span><span class="sxs-lookup"><span data-stu-id="bd0f6-108">Service</span></span>

<span data-ttu-id="bd0f6-109">Ce projet contient un service de calculatrice auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="bd0f6-110">Dans la méthode `Main`, un hôte de service est créé et un point de terminaison de service lui est ajouté.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="bd0f6-111">Ensuite, un <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> est créé.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="bd0f6-112">Pour activer les annonces, un point de terminaison d'annonce doit être ajouté au <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="bd0f6-113">Dans ce cas, un point de terminaison standard utilisant la multidiffusion UDP est ajouté comme point de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="bd0f6-114">Celui-ci diffuse les annonces sur une adresse UDP bien connue.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-114">This broadcasts the announcements over a well-known UDP address.</span></span>

```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);

     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();

     // Announce the availability of the service over UDP multicast
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());

    // Make the service discoverable over UDP multicast.
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());
    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="bd0f6-115">Client</span><span class="sxs-lookup"><span data-stu-id="bd0f6-115">Client</span></span>

<span data-ttu-id="bd0f6-116">Dans ce projet, notez que le client héberge un <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="bd0f6-117">En outre, deux délégués sont inscrits avec les événements.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="bd0f6-118">Ces événements déterminent les actions du client lors de la réception d'annonces en ligne et hors connexion.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="bd0f6-119">Les méthodes `OnOnlineEvent` et `OnOfflineEvent` gèrent respectivement les messages d'annonce de type Hello et Bye.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="bd0f6-120">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="bd0f6-120">To use this sample</span></span>

1. <span data-ttu-id="bd0f6-121">Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="bd0f6-122">Pour plus d’informations, consultez [configuration de http et HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="bd0f6-122">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="bd0f6-123">L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="bd0f6-124">Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="bd0f6-125">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-125">Build the solution.</span></span>

3. <span data-ttu-id="bd0f6-126">Exécutez l'application client.exe.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-126">Run the client.exe application.</span></span>

4. <span data-ttu-id="bd0f6-127">Exécutez l'application service.exe.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-127">Run the service.exe application.</span></span> <span data-ttu-id="bd0f6-128">Notez que le client reçoit une annonce en ligne.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-128">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="bd0f6-129">Fermez l'application service.exe.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-129">Close the service.exe application.</span></span> <span data-ttu-id="bd0f6-130">Notez que le client reçoit une annonce hors connexion.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-130">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd0f6-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd0f6-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bd0f6-133">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd0f6-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd0f6-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="bd0f6-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
