---
title: Annonces de découverte et client d'annonce
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040180"
---
# <a name="discovery-announcements-and-announcement-client"></a>Annonces de découverte et client d'annonce

La fonctionnalité de découverte WCF permet aux composants d’annoncer leur disponibilité. S'il est configuré pour, un service envoie des annonces de type Hello et Bye. Les clients ou d'autres composants peuvent écouter les messages d'annonce de ce type et agir dessus. Cela offre une autre méthode aux clients pour être informés des services. Les fonctionnalités d'annonce ont plusieurs utilisations, par exemple, si les services entrent dans un réseau et le quittent fréquemment, les annonces peuvent constituer une meilleure solution que de rechercher des services. Avec cette approche, le trafic réseau est réduit et le client peut être informé de la présence ou du départ du service dès la réception des annonces.

## <a name="discovery-announcements"></a>Annonces de découverte

Lorsqu'un service configuré pour les annonces rejoint un réseau et devient détectable, il envoie un message de type Hello qui annonce sa disponibilité aux clients qui écoutent. Le message contient les informations sur le service liées à la découverte, tel que son contrat, l'adresse du point de terminaison et les étendues associées. Vous pouvez spécifier où est envoyé le message d'annonce à l'aide de la classe <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Si le point de terminaison d'annonce est un objet <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, les messages de types Hello et Bye sont envoyés en mode multidiffusion de manière appropriée, ou si le point de terminaison d'annonce est en mode monodiffusion, les messages sont envoyés directement au point de terminaison spécifié.

> [!NOTE]
> Les annonces sont envoyées lors de l'ouverture et de la fermeture de l'hôte de service. Si ces appels ne se terminent pas correctement, le message d'annonce peut ne pas être envoyé. Par exemple si le service est défaillant, le message d'annonce de type Bye n'est pas envoyé.

> [!TIP]
> Vous pouvez personnaliser les fonctionnalités d'annonce, ce qui vous permet d'envoyer des annonces quand vous le souhaitez.

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] définit les points de terminaison <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> et <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> comme points de terminaison standard pour permettre aux services et aux clients d'envoyer facilement des annonces de type Hello et Bye.

### <a name="announcements-on-the-service"></a>Annonces sur le service

Pour configurer le service pour envoyer des annonces, ajoutez un <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> avec un point de terminaison d'annonce. L'exemple suivant indique comment ajouter ce comportement par programme à l'hôte de service. Cet exemple utilise `UdpAnnouncementEndpoint`, ce qui implique que les annonces sont envoyées en mode multidiffusion à un emplacement spécifié par ce point de terminaison de standard.

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

Le comportement peut également être configuré dans le fichier de configuration, comme indiqué dans l'exemple suivant.

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

Les exemples précédents configurent un service pour envoyer automatiquement des messages d'annonce. Vous pouvez également envoyer explicitement des messages d'annonce à l'aide de la classe <xref:System.ServiceModel.Discovery.AnnouncementClient>.

### <a name="announcements-on-the-client"></a>Annonces sur le client

Une application cliente doit héberger un service d'annonce pour répondre aux messages de type Hello et Bye et s'abonner aux événements <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> et <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived>. L'exemple suivant montre comment effectuer cette opération.

```csharp
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

Lorsqu'un message de type Hello ou Bye est reçu, vous pouvez accéder aux métadonnées de découverte du point de terminaison via <xref:System.ServiceModel.Discovery.AnnouncementEventArgs>, comme indiqué dans l'exemple suivant.

```csharp
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
