---
title: Modèle objet de découverte WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: 06984766fa8199a18197255c57492863a888e3aa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281935"
---
# <a name="wcf-discovery-object-model"></a>Modèle objet de découverte WCF

La découverte WCF consiste en un jeu de types fournissant un modèle de programmation unifié qui permet de développer des services détectables au moment de l'exécution et des clients qui recherchent et utilisent ces services.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Rendre un service détectable et rechercher des services  

 Pour rendre un service WCF détectable, ajoutez un objet <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> à l'objet <xref:System.ServiceModel.Description.ServiceDescription> de l'hôte de service et ajoutez un point de terminaison de découverte. Si un service est configuré pour envoyer des messages d'annonce (en ajoutant un objet <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) l'annonce est envoyée lors de l'ouverture et de la fermeture de l'hôte de service.  
  
 Un client qui souhaite écouter des messages d'annonce du service héberge un service d'annonce et ajoute un ou plusieurs points de terminaison d'annonce. Le service d'annonce reçoit des messages d'annonce et déclenche des événements d'annonce.  
  
 Un client utilise la classe <xref:System.ServiceModel.Discovery.DiscoveryClient> pour rechercher des services disponibles. L'application cliente instancie la classe <xref:System.ServiceModel.Discovery.DiscoveryClient>, en transmettant un point de terminaison de découverte qui spécifie où envoyer des messages de découverte. Le client appelle la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, qui envoie une demande `Probe`. Les services qui écoutent les messages de découverte reçoivent ces demandes `Probe`. Si le service correspond aux critères spécifiés dans le `Probe`, il renvoie un message `ProbeMatch` au client.  
  
## <a name="object-model"></a>Modèle objet  

 L'API de découverte WCF définit les classes suivantes :  
  
- <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
- <xref:System.ServiceModel.Discovery.FindCriteria>  
  
- <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
- <xref:System.ServiceModel.Discovery.FindResponse>  
  
- <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
- <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  

 La classe <xref:System.ServiceModel.Discovery.AnnouncementClient> fournit des méthodes synchrones et asynchrones pour l’envoi de messages d’annonce. Il existe deux types de messages d'annonce, Hello et Bye. Un message de type Hello est envoyé pour indiquer qu'un service est devenu disponible et un message de type Bye est envoyé pour indiquer qu'un service existant est devenu indisponible. Le développeur crée une instance <xref:System.ServiceModel.Discovery.AnnouncementClient>, en passant une instance de <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> comme paramètre de constructeur.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  

 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> représente un point de terminaison standard avec un contrat d'annonce fixe. Il est utilisé par un service ou un client pour envoyer et recevoir des messages d'annonce. Par défaut, la classe <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> est définie pour utiliser la version 11 du protocole WS_Discovery.  
  
## <a name="announcementservice"></a>AnnouncementService  

 <xref:System.ServiceModel.Discovery.AnnouncementService> est une implémentation fournie par le système d'un service d'annonce qui reçoit et traite des messages d'annonce. Lors de la réception d'un message de type Hello ou Bye, l'instance <xref:System.ServiceModel.Discovery.AnnouncementService> appelle la méthode virtuelle appropriée <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> ou <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, qui déclenche des événements d'annonce.  
  
## <a name="discoveryclient"></a>DiscoveryClient  

 La classe <xref:System.ServiceModel.Discovery.DiscoveryClient> est utilisée par une application cliente pour rechercher et résoudre les services disponibles. Elle fournit des méthodes synchrone et asynchrones pour la recherche et la résolution de services, en fonction des objets spécifiés <xref:System.ServiceModel.Discovery.FindCriteria> et <xref:System.ServiceModel.Discovery.ResolveCriteria>, respectivement. Le développeur crée une instance <xref:System.ServiceModel.Discovery.DiscoveryClient> et fournit une instance de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> comme paramètre de constructeur.  
  
 Pour rechercher un service, le développeur appelle la méthode `Find` synchrone ou asynchrone, qui fournit une instance <xref:System.ServiceModel.Discovery.FindCriteria> contenant les critères de recherche à utiliser. L'objet <xref:System.ServiceModel.Discovery.DiscoveryClient> crée un message `Probe` avec les en-têtes appropriés et envoie la demande de recherche. Comme il peut y avoir plusieurs demandes `Find` en attente n'importe quand, le client met en corrélation les réponses reçues et valide la réponse. Puis il remet les résultats à l'appelant de l'opération `Find`, à l'aide de <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Pour résoudre un service connu, le développeur appelle la méthode `Resolve` synchrone ou asynchrone qui fournit une instance de <xref:System.ServiceModel.Discovery.ResolveCriteria> contenant l’ <xref:System.ServiceModel.EndpointAddress> du service connu. L'objet <xref:System.ServiceModel.Discovery.DiscoveryClient> crée le message `Resolve` avec les en-têtes appropriés et envoie la demande de résolution. La réponse reçue est mise en corrélation par rapport aux demandes de résolution en attente et le résultat est remis à l'appelant de l'opération `Resolve`, à l'aide de l'objet <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Si un proxy de découverte est présent sur le réseau et que le <xref:System.ServiceModel.Discovery.DiscoveryClient> envoie la demande de découverte en mode multidiffusion, le proxy de découverte peut répondre par le message de suppression de multidiffusion de type Hello. Le <xref:System.ServiceModel.Discovery.DiscoveryClient> déclenche l'événement `ProxyAvailable` lorsqu'il reçoit des messages de type Hello en réponse à des demandes `Find` ou `Resolve` en attente. L'événement `ProxyAvailable` contient le <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> sur le proxy de découverte. Il incombe au développeur d'utiliser ces informations pour basculer du mode ad hoc au mode managé.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  

 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> représente un point de terminaison standard avec un contrat de découverte fixe. Il est utilisé par un service ou un client pour envoyer ou recevoir des messages de découverte. Par défaut, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> est défini pour utiliser le mode <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> et la version 11 du protocole WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  

 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> est utilisé pour générer un <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> lorsque le service envoie des messages de découverte ou d'annonce.  
  
## <a name="discoveryservice"></a>DiscoveryService  

 La classe abstraite <xref:System.ServiceModel.Discovery.DiscoveryService> fournit une infrastructure pour recevoir et traiter des messages `Probe` et `Resolve`. Lors de la réception d'un message `Probe`, <xref:System.ServiceModel.Discovery.DiscoveryService> crée une instance de <xref:System.ServiceModel.Discovery.FindRequestContext> basée sur le message entrant et appelle la méthode virtuelle <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A>. Lors de la réception d'un message `Resolve`, <xref:System.ServiceModel.Discovery.DiscoveryService> appelle la méthode virtuelle <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A>. Vous pouvez hériter de cette classe pour fournir une implémentation personnalisée du service de découverte.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  

 La classe abstraite <xref:System.ServiceModel.Discovery.DiscoveryProxy> fournit une infrastructure pour recevoir et traiter les messages de découverte et d'annonce. Vous héritez de cette classe lorsque vous implémentez un proxy de découverte personnalisé. Lorsqu'un message `Probe` est reçu en multidiffusion, la classe <xref:System.ServiceModel.Discovery.DiscoveryProxy> appelle la méthode virtuelle `BeginShouldRedirectFind` pour déterminer si un message de suppression de multidiffusion doit être envoyé. Si le développeur décide de ne pas envoyer de message de suppression de multidiffusion ou si le message `Probe` a été reçu en monodiffusion, il crée une instance de la classe <xref:System.ServiceModel.Discovery.FindRequestContext> basée sur le message entrant et appelle la méthode virtuelle `OnBeginFind`. Lorsqu'un message `Resolve` est reçu en multidiffusion, la classe <xref:System.ServiceModel.Discovery.DiscoveryProxy> appelle la méthode virtuelle `ShouldRedirectResolve` pour déterminer si un message de suppression de multidiffusion doit être envoyé. Si le développeur décide de ne pas envoyer de message de suppression de multidiffusion ou si le message `Resolve` a été reçu en monodiffusion, il crée une instance de la classe <xref:System.ServiceModel.Discovery.ResolveCriteria> basée sur le message entrant et appelle la méthode virtuelle `OnBeginResolve`. Lors de la réception d'un message de type Hello ou Bye, <xref:System.ServiceModel.Discovery.DiscoveryProxy> appelle la méthode virtuelle appropriée (`OnBeginOnlineAnnouncement` ou `OnBeingOfflineAnnouncement`), qui déclenche des événements d'annonce.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  

 La classe <xref:System.ServiceModel.Discovery.DiscoveryVersion> représente la version du protocole de découverte à utiliser.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  

 La classe <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est utilisée pour contrôler la détectabilité d’un point de terminaison, spécifier les extensions, les noms supplémentaires de type de contrat. et les étendues associées à ce point de terminaison. Ce comportement est ajouté à un point de terminaison d'application pour configurer son <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Lorsque <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> est ajouté à l'hôte de service, tous les points de terminaison d'application hébergés par défaut par l'hôte de service deviennent détectables. Le développeur peut désactiver la découverte pour un point de terminaison spécifique en définissant la propriété <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> sur `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  

 La classe <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> fournit une représentation d'un point de terminaison publié par le service, de manière indépendante de la version. Elle contient des adresses du point de terminaison, des URI d’écoute, des noms de type de contrat, des étendues, une version de métadonnées et des extensions spécifiés par le développeur de service. Le <xref:System.ServiceModel.Discovery.FindCriteria> envoyé par le client lors d'une opération `Probe` est comparé au <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Si les critères correspondent, le <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> est retourné au client. L'adresse du point de terminaison dans <xref:System.ServiceModel.Discovery.ResolveCriteria> est comparée à l'adresse du point de terminaison de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Si les critères correspondent, le <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> est retourné au client.  
  
## <a name="findcriteria"></a>FindCriteria  

 La classe <xref:System.ServiceModel.Discovery.FindCriteria> est une classe indépendante de la version, qui permet de spécifier les critères utilisés lors de la recherche d'un service. Elle prend entièrement en charge les critères définis par WS-Discovery pour correspondre aux services. Elle possède également des extensions qui permettent aux développeurs de spécifier des valeurs personnalisées qui peuvent être utilisées lors du processus de mise en correspondance. Le développeur peut fournir les critères d'arrêt pour l'opération `Find` en spécifiant la propriété <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, qui indique le nombre total de services recherchés par le développeur ou spécifie la valeur <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, qui correspond à la durée pendant laquelle le client attend des réponses.  
  
## <a name="findrequestcontext"></a>FindRequestContext  

 La classe <xref:System.ServiceModel.Discovery.FindRequestContext> est instanciée par le service de découverte en fonction du message `Probe` qu'il reçoit lorsqu'un client initialise une opération `Find`. Il contient une instance de <xref:System.ServiceModel.Discovery.FindCriteria> qui a été spécifiée par le client.  
  
## <a name="findresponse"></a>FindResponse  

 La classe <xref:System.ServiceModel.Discovery.FindResponse> est retournée par l'appelant de la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> avec les réponses de l'opération `Find`. Elle est également présente dans <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Elle contient une collection <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, qui est la collection des points de terminaison découverts et un dictionnaire d’objets <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> et <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  

 La classe <xref:System.ServiceModel.Discovery.ResolveCriteria> est une classe indépendante de la version qui permet de spécifier les critères utilisés lors de la résolution d'un service déjà connu. Elle contient l'adresse du point de terminaison du service connu. Le développeur peut fournir les critères d'arrêt pour l'opération de résolution en spécifiant la propriété <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, qui indique combien de temps le client attend des réponses.  
  
## <a name="resolveresponse"></a>ResolveResponse  

 La classe <xref:System.ServiceModel.Discovery.ResolveResponse> est retournée par l'appelant de la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> avec la réponse de l'opération `Resolve`. Elle est également présente dans <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Elle contient une instance de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, qui correspond aux points de terminaison découverts et une instance de <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  

 La classe <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> permet au développeur d'ajouter à un service la fonctionnalité de découverte. Vous ajoutez ce comportement à l'objet <xref:System.ServiceModel.ServiceHost>. La classe <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> effectue une itération sur les points de terminaison d’application ajoutés à l’hôte de service et crée une collection d’objets <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> à partir des points de terminaison détectables. Tous les points de terminaison sont détectables par défaut. La détectabilité d'un point de terminaison particulier peut être contrôlée en ajoutant l'objet <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> à ce point de terminaison particulier. Si des points de terminaison d'annonce sont ajoutés à l'objet <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>, l'annonce de tous les points de terminaison détectables est envoyée sur chacun des points de terminaison d'annonce lors de l'ouverture et de la fermeture de l'hôte de service.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  

 La classe <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> est un point de terminaison d’annonce standard, préconfiguré pour l’annonce sur une liaison de multidiffusion UDP. Par défaut, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> est définie pour utiliser la version d'avril 2005 du protocole WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  

 La classe <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est un point de terminaison de découverte standard, préconfiguré pour la découverte sur une liaison de multidiffusion UDP. Par défaut, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> est définie pour utiliser la version 11 du protocole WS-Discovery et le mode <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType>.
