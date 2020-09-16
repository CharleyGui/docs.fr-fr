---
title: Vue d'ensemble de la découverte WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 8b4dda410b9ca7d7d3ff76795753811a80a617ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554617"
---
# <a name="wcf-discovery-overview"></a>Vue d'ensemble de la découverte WCF
Les API de découverte offrent un modèle de programmation unifié pour la publication et la découverte dynamiques de services Web, à l'aide du protocole WS-Discovery. Ces API permettent aux services de se publier eux-mêmes et permettent aux clients de rechercher des services publiés. Une fois un service rendu détectable, le service a la capacité d'envoyer des messages d'annonce, ainsi que d'écouter des demandes de découverte et d'y répondre. Les services détectables peuvent envoyer des messages de type Hello pour annoncer leur arrivée sur un réseau et des messages de type Bye pour annoncer leur départ d'un réseau. Pour trouver un service, les clients envoient une demande `Probe` qui contient des critères spécifiques tels que le type de contrat de service, les mots clés et l'étendue sur le réseau. Les services reçoivent la demande `Probe` et déterminent s'ils correspondent aux critères. Si un service correspond, il répond en renvoyant au client un message `ProbeMatch`, avec les informations nécessaires pour contacter le service. Les clients peuvent également envoyer des demandes `Resolve` qui leur permettent de trouver des services dont l'adresse du point de terminaison risque d'avoir été modifiée. Les services correspondants répondent aux demandes `Resolve` en renvoyant un message `ResolveMatch` au client.  
  
## <a name="ad-hoc-and-managed-modes"></a>Modes ad hoc et managé  
 L'API de découverte prend en charge deux modes différents : managé et ad hoc. Dans le mode managé, un serveur centralisé, appelé proxy de découverte, gère des informations sur les services disponibles. Le proxy de découverte peut être rempli des informations sur les services de diverses manières. Par exemple, les services peuvent envoyer au proxy de découverte des messages d'annonce lors du démarrage, ou le proxy peut lire les données d'une base de données ou d'un fichier de configuration pour déterminer quels services sont disponibles. La manière dont le proxy de découverte est rempli dépend entièrement du développeur. Les clients utilisent le proxy de découverte pour récupérer des informations concernant les services disponibles. Lorsqu'un client recherche un service, il envoie un message `Probe` au proxy de découverte et le proxy détermine si l'un des services qu'il connaît correspond au service recherché par le client. S'il existe des correspondances, le proxy de découverte renvoie au client une réponse `ProbeMatch`. Le client peut ensuite contacter directement le service à l'aide des informations de service retournées par le proxy. Le principe essentiel du mode managé est que les demandes de découverte sont envoyées en mode monodiffusion à une autorité, le proxy de découverte. Le .NET Framework contient des composants clés qui vous permettent de générer votre propre proxy. Les clients et les services peuvent trouver le proxy selon plusieurs méthodes :  
  
- Le proxy peut répondre aux messages ad hoc.  
  
- Le proxy peut envoyer un message d'annonce lors du démarrage.  
  
- Les clients et les services peuvent être écrits de manière à rechercher un point de terminaison connu spécifique.  
  
 En mode ad hoc, il n'existe aucun serveur centralisé. Tous les messages de découverte, tels que les annonces de service et les demandes du client, sont envoyés en mode multidiffusion. Par défaut, le .NET Framework contient une prise en charge de la découverte ad hoc sur le protocole UDP. Par exemple, si un service est configuré pour envoyer une annonce de type Hello lors du démarrage, il l'envoie à une adresse de multidiffusion connue, à l'aide du protocole UDP. Les clients doivent écouter activement ces annonces et les traiter en conséquence. Lorsqu'un client envoie un message `Probe` pour un service, ce message est envoyé sur le réseau à l'aide d'un protocole de multidiffusion. Chaque service qui reçoit la demande détermine s'il correspond aux critères du message `Probe`, puis répond directement au client avec un message `ProbeMatch` si le service correspond aux critères spécifiés dans le message `Probe`.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Avantages de l'utilisation de la découverte WCF  
 Comme la découverte WCF est implémentée à l'aide du protocole WS-Discovery, elle est interopérable avec les autres clients, services et proxys qui implémentent également WS-Discovery. La découverte WCF repose sur les API WCF existantes, ce qui permet d'ajouter facilement des fonctionnalités de découverte à vos services et vos clients existants. La détectabilité de service peut être ajoutée facilement via les paramètres de configuration de l'application. De plus, la découverte WCF prend également en charge l'utilisation du protocole de découverte sur d'autres transports, tels qu'un réseau homologue, une superposition d'affectation des noms et HTTP. La découverte WCF offre la prise en charge d'un mode d'opération managé où un proxy de découverte est utilisé. Cela permet de réduire le trafic réseau puisque les messages sont envoyés directement au proxy de découverte plutôt que d'envoyer des messages de multidiffusion au réseau entier. La découverte WCF permet également davantage de flexibilité lors de l'utilisation des services Web. Par exemple, vous pouvez modifier l'adresse d'un service sans avoir à reconfigurer le client ou le service. Lorsqu'un client doit accéder au service, il peut émettre un message `Probe` via une demande `Find` et attendre que le service réponde avec son adresse actuelle. La découverte WCF permet à un client de rechercher un service en fonction de différents critères, notamment les types de contrat, les éléments de liaison, l'espace de noms, l'étendue et les mots clés ou les numéros de version. La découverte WCF permet l'exécution et la découverte au moment de la conception. L'ajout de la découverte à votre application peut également permettre d'activer d'autres scénarios, tels que la tolérance aux pannes et la configuration automatique.  
  
## <a name="service-publication"></a>Publication de service  
 Pour rendre un service détectable, il est nécessaire d'ajouter un objet <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> à l'hôte de service, ainsi qu'un point de terminaison de découverte pour spécifier l'endroit où écouter les messages de découverte. L'exemple de code suivant montre comment modifier un service auto-hébergé pour le rendre détectable.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 Une instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> doit être ajoutée à une description du service pour rendre le service détectable. Une instance <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> doit être ajoutée à l'hôte de service pour indiquer au service où écouter les demandes de découverte. Dans cet exemple, un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (dérivé de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) est ajouté pour spécifier que le service doit écouter les demandes de découverte sur le transport de multidiffusion UDP. L'objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est utilisé pour la découverte ad hoc parce que tous les messages sont envoyés en mode multidiffusion.  
  
## <a name="announcement"></a>Annonce  
 Par défaut, la publication de service n'envoie pas de messages d'annonce. Le service doit être configuré pour envoyer des messages d'annonce. Cela offre aux développeurs de service une flexibilité supplémentaire, parce qu'ils peuvent annoncer le service séparément de l'écoute des messages de découverte. L'annonce de service peut également être utilisée comme mécanisme d'inscription des services avec un proxy de découverte ou d'autres registres de service. Le code suivant indique comment configurer un service pour envoyer des messages d’annonce sur une liaison UDP.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>Découverte de service  
 Une application cliente peut utiliser la classe <xref:System.ServiceModel.Discovery.DiscoveryClient> pour rechercher des services. Le développeur crée une instance de la classe <xref:System.ServiceModel.Discovery.DiscoveryClient> qui est transmise à un point de terminaison de découverte qui spécifie où envoyer des messages `Probe` ou `Resolve`. Le client appelle ensuite la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> qui spécifie des critères de recherche dans une instance <xref:System.ServiceModel.Discovery.FindCriteria>. Si des services correspondants sont trouvés, la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> retourne une collection d'objets <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Le code suivant indique comment appeler la méthode `Find`, puis se connecter à un service découvert.  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>Découverte et sécurité de niveau message  
 Lors de l'utilisation de la sécurité de niveau message, il est nécessaire de spécifier un objet <xref:System.ServiceModel.EndpointIdentity> sur le point de terminaison de découverte du service et un objet <xref:System.ServiceModel.EndpointIdentity> correspondant sur le point de terminaison de découverte client. Pour plus d’informations sur la sécurité au niveau des messages, consultez [sécurité des messages](message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Services de découverte et hébergés Web  
 Pour que les services WCF soient détectables, ils doivent être en cours d'exécution. Les services WCF hébergés sous IIS ou WAS ne sont pas exécutés tant que IIS/WAS ne reçoit pas de message lié pour le service, ainsi, ils ne sont pas détectables par défaut.  Il existe deux options pour rendre les services hébergés Web détectables :  
  
1. Utiliser la fonctionnalité de démarrage automatique de Windows Server AppFabric  
  
2. Utiliser un proxy de découverte pour communiquer pour le compte du service  
  
 Windows Server AppFabric possède une fonctionnalité de démarrage automatique qui permet de démarrer un service avant de recevoir des messages. Lorsque cette fonction de démarrage automatique est définie, un service hébergé IIS/WAS peut être configuré pour être détecté. Pour plus d’informations sur la fonctionnalité de démarrage automatique, consultez [fonctionnalité de démarrage automatique de Windows Server AppFabric](/previous-versions/appfabric/ee677260(v=azure.10)). En plus de l’activation de la fonctionnalité de démarrage automatique, vous devez configurer le service pour la découverte. Pour plus d’informations, consultez [Comment : ajouter par programmation la détectabilité à un service WCF et client](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[configuration de la découverte dans un fichier de configuration](configuring-discovery-in-a-configuration-file.md).  
  
 Un proxy de découverte peut être utilisé pour communiquer pour le compte du service WCF lorsque le service n'est pas exécuté. Le proxy peut écouter la sonde ou résoudre des messages et répondre au client. Le client peut ensuite envoyer des messages directement au service. Lorsque le client envoie un message au service, il est instancié pour répondre au message. Pour plus d’informations sur l’implémentation d’un proxy de découverte, consultez [implémentation d’un proxy de découverte](implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Pour que la découverte WCF fonctionne correctement, toutes les cartes réseau (contrôleur d’interface réseau) ne doivent avoir qu’une seule adresse IP.
