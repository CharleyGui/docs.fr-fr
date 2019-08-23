---
title: Configuration de services WCF dans le code
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 699549305ce8ca17480285e33570c01d00c7cb97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948430"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="a99a9-102">Configuration de services WCF dans le code</span><span class="sxs-lookup"><span data-stu-id="a99a9-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="a99a9-103">Windows Communication Foundation (WCF) permet aux développeurs de configurer des services à l’aide de fichiers de configuration ou de code.</span><span class="sxs-lookup"><span data-stu-id="a99a9-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="a99a9-104">Les fichiers de configuration sont utiles lorsqu'un service doit être configuré après avoir été déployé.</span><span class="sxs-lookup"><span data-stu-id="a99a9-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="a99a9-105">Lorsqu'il utilise des fichiers de configuration, un professionnel de l'informatique doit uniquement mettre à jour le fichier de configuration, aucune recompilation n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a99a9-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="a99a9-106">Les fichiers de configuration, toutefois, peuvent être complexes et difficiles à gérer.</span><span class="sxs-lookup"><span data-stu-id="a99a9-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="a99a9-107">Il n'existe aucune prise en charge du débogage de fichiers de configuration et les éléments de configuration sont référencés par des noms. La création de fichiers de configuration est donc susceptible d'engendrer des erreurs et difficile.</span><span class="sxs-lookup"><span data-stu-id="a99a9-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="a99a9-108">WCF vous permet également de configurer des services dans le code.</span><span class="sxs-lookup"><span data-stu-id="a99a9-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="a99a9-109">Dans les versions précédentes de WCF (4,0 et versions antérieures) la configuration des services dans le code était facile dans les scénarios <xref:System.ServiceModel.ServiceHost> auto-hébergés, la classe vous permettait de configurer des points de terminaison et des comportements avant d’appeler ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="a99a9-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="a99a9-110">Dans les scénarios hébergés sur le Web, toutefois, vous n'avez pas accès direct à la classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a99a9-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="a99a9-111">Pour configurer un service hébergé sur le Web vous deviez créer un `System.ServiceModel.ServiceHostFactory` qui créait le <xref:System.ServiceModel.Activation.ServiceHostFactory> et effectuait la configuration nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a99a9-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="a99a9-112">À compter de .NET 4,5, WCF offre un moyen plus simple de configurer des services auto-hébergés et hébergés sur le Web dans le code.</span><span class="sxs-lookup"><span data-stu-id="a99a9-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="a99a9-113">Méthode Configure</span><span class="sxs-lookup"><span data-stu-id="a99a9-113">The Configure method</span></span>  
 <span data-ttu-id="a99a9-114">Il suffit de définir une méthode statique publique appelée `Configure` avec la signature suivante dans votre classe d'implémentation de service :</span><span class="sxs-lookup"><span data-stu-id="a99a9-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="a99a9-115">La méthode Configure prend une instance <xref:System.ServiceModel.ServiceConfiguration> qui permet au développeur d'ajouter des points de terminaison et des comportements.</span><span class="sxs-lookup"><span data-stu-id="a99a9-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="a99a9-116">Cette méthode est appelée par WCF avant l’ouverture de l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a99a9-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="a99a9-117">S'ils sont définis, les paramètres de configuration du service spécifiés dans un fichier app.config ou web.config sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="a99a9-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="a99a9-118">L'extrait de code suivant montre comment définir la méthode `Configure` et ajouter un point de terminaison de service, un comportement de point de terminaison et des comportements de service :</span><span class="sxs-lookup"><span data-stu-id="a99a9-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="a99a9-119">Pour activer un protocole tel que https pour un service, vous pouvez soit ajouter explicitement un point de terminaison qui utilise le protocole ou vous pouvez ajouter automatiquement des points de terminaison en appelant ServiceConfiguration.EnableProtocol (Binding) qui ajoute un point de terminaison pour chaque adresse de base compatible avec le protocole et chaque contrat de service défini.</span><span class="sxs-lookup"><span data-stu-id="a99a9-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="a99a9-120">L'exemple de code suivant illustre l'utilisation de la méthode ServiceConfiguration.EnableProtocol :</span><span class="sxs-lookup"><span data-stu-id="a99a9-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="a99a9-121">Les paramètres de la section`protocolMappings`> < sont utilisés uniquement si aucun point <xref:System.ServiceModel.ServiceConfiguration> de terminaison d’application n’est ajouté par programmation à. Vous pouvez éventuellement charger la configuration du service à partir du fichier de configuration de l' <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> application par défaut en appelant, puis modifier les paramètres.</span><span class="sxs-lookup"><span data-stu-id="a99a9-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="a99a9-122">La classe <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> vous permet également de charger la configuration à partir d'une configuration centralisée.</span><span class="sxs-lookup"><span data-stu-id="a99a9-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="a99a9-123">Le code suivant illustre comment implémenter cela :</span><span class="sxs-lookup"><span data-stu-id="a99a9-123">The following code illustrates how to implement this:</span></span>  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="a99a9-124">Notez que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignore <`host`paramètres de > dans la`service`balise de >`system.serviceModel`< de < >.</span><span class="sxs-lookup"><span data-stu-id="a99a9-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="a99a9-125">Conceptuellement, <`host`> concerne la configuration de l’hôte, et non la configuration du service, et il est chargé avant l’exécution de la méthode de configuration.</span><span class="sxs-lookup"><span data-stu-id="a99a9-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99a9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a99a9-126">See also</span></span>

- [<span data-ttu-id="a99a9-127">Configuration des services à l’aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="a99a9-128">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="a99a9-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="a99a9-129">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="a99a9-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="a99a9-130">Configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-130">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)
- [<span data-ttu-id="a99a9-131">Activation basée sur la configuration dans les services IIS et WAS</span><span class="sxs-lookup"><span data-stu-id="a99a9-131">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="a99a9-132">Prise en charge de la configuration et des métadonnées</span><span class="sxs-lookup"><span data-stu-id="a99a9-132">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="a99a9-133">Configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-133">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="a99a9-134">Guide pratique pour Spécifier une liaison de service dans la configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-134">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="a99a9-135">Guide pratique : Créer un point de terminaison de service dans la configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-135">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="a99a9-136">Guide pratique pour Publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="a99a9-137">Guide pratique pour Spécifier une liaison de client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="a99a9-137">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
