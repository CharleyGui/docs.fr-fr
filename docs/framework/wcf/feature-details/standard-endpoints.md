---
title: Points de terminaison standard
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 48924e06457cf9f91ce4f900bb38de4d22bfc550
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463777"
---
# <a name="standard-endpoints"></a><span data-ttu-id="6b700-102">Points de terminaison standard</span><span class="sxs-lookup"><span data-stu-id="6b700-102">Standard Endpoints</span></span>
<span data-ttu-id="6b700-103">Les points de terminaison sont définis en spécifiant une adresse, une liaison et un contrat.</span><span class="sxs-lookup"><span data-stu-id="6b700-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="6b700-104">Les autres paramètres qui peuvent être définis sur un point de terminaison incluent la configuration du comportement, les en-têtes, et les URI d'écoute.</span><span class="sxs-lookup"><span data-stu-id="6b700-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="6b700-105">Pour certains types de points de terminaison, ces valeurs ne changent pas.</span><span class="sxs-lookup"><span data-stu-id="6b700-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="6b700-106">Par exemple, les points de terminaison d'échange de métadonnées utilisent toujours le contrat <xref:System.ServiceModel.Description.IMetadataExchange>.</span><span class="sxs-lookup"><span data-stu-id="6b700-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="6b700-107">D'autres points de terminaison, tels que <xref:System.ServiceModel.Description.WebHttpEndpoint>, requièrent toujours un comportement de point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b700-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="6b700-108">L'utilisation d'un point de terminaison peut être simplifiée par l'emploi de points de terminaison possédant des valeurs par défaut pour des propriétés de point de terminaison courantes.</span><span class="sxs-lookup"><span data-stu-id="6b700-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="6b700-109">Les points de terminaison standard permettent à un développeur de définir un point de terminaison avec des valeurs par défaut ou dont une ou plusieurs propriétés de point de terminaison restent inchangées.</span><span class="sxs-lookup"><span data-stu-id="6b700-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="6b700-110">Les points de terminaison de ce type vous permettent d'utiliser un point de terminaison sans avoir à spécifier les informations qui sont de nature statique.</span><span class="sxs-lookup"><span data-stu-id="6b700-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="6b700-111">Les points de terminaison standard peuvent être utilisés comme points de terminaison d'infrastructure et d'application.</span><span class="sxs-lookup"><span data-stu-id="6b700-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="6b700-112">Points de terminaison d'infrastructure</span><span class="sxs-lookup"><span data-stu-id="6b700-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="6b700-113">Un service peut exposer des points de terminaison dont certaines des propriétés n'ont pas été implémentées de manière explicite par l'auteur du service.</span><span class="sxs-lookup"><span data-stu-id="6b700-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="6b700-114">Par exemple, le point de terminaison d'échange de métadonnées expose le contrat <xref:System.ServiceModel.Description.IMetadataExchange>, mais vous n'implémentez pas cette interface en tant qu'auteur du service, elle est implémentée par WCF.</span><span class="sxs-lookup"><span data-stu-id="6b700-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="6b700-115">Ces points de terminaison d'infrastructure ont des valeurs par défaut pour une ou plusieurs propriétés de point de terminaison, dont certaines peuvent être immuables.</span><span class="sxs-lookup"><span data-stu-id="6b700-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="6b700-116">La propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> du point de terminaison d'échange de métadonnées doit être <xref:System.ServiceModel.Description.IMetadataExchange>, tandis que d'autres propriétés comme la liaison peuvent être fournies par le développeur.</span><span class="sxs-lookup"><span data-stu-id="6b700-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="6b700-117">Les points de terminaison d'infrastructure sont identifiés en attribuant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6b700-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="6b700-118">Points de terminaison d'application</span><span class="sxs-lookup"><span data-stu-id="6b700-118">Application Endpoints</span></span>  
 <span data-ttu-id="6b700-119">Les développeurs d’applications peuvent définir leurs propres points de terminaison standard qui spécifient des valeurs par défaut pour l’adresse, la liaison ou le contrat.</span><span class="sxs-lookup"><span data-stu-id="6b700-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="6b700-120">Vous définissez un point de terminaison standard en dérivant une classe de <xref:System.ServiceModel.Description.ServiceEndpoint> et en définissant les propriétés de point de terminaison appropriées.</span><span class="sxs-lookup"><span data-stu-id="6b700-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="6b700-121">Vous pouvez fournir des valeurs par défaut pour les propriétés qui peuvent être modifiées.</span><span class="sxs-lookup"><span data-stu-id="6b700-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="6b700-122">D'autres propriétés ont des valeurs statiques qui ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="6b700-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="6b700-123">L'exemple suivant indique comment implémenter un point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="6b700-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="6b700-124">Pour utiliser un point de terminaison personnalisé défini par <xref:System.ServiceModel.Configuration.StandardEndpointElement>l’utilisateur <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>dans un fichier de configuration, vous devez tirer une classe de , tirer une classe de , et enregistrer le nouveau point de terminaison standard dans la section extensions dans app.config ou machine.config.  Le <xref:System.ServiceModel.Configuration.StandardEndpointElement> fournit une prise en charge de configuration pour le point de terminaison standard, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6b700-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="6b700-125">Le <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> fournit le type de support pour la `standardEndpoints` collection qui apparaît sous la section <> dans la configuration pour le point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="6b700-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="6b700-126">L'exemple suivant montre comment implémenter cette classe.</span><span class="sxs-lookup"><span data-stu-id="6b700-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="6b700-127">L’exemple suivant montre comment enregistrer un point de terminaison standard dans la section des extensions.</span><span class="sxs-lookup"><span data-stu-id="6b700-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
      </standardEndpointExtensions>
</extensions>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="6b700-128">Configuration d'un point de terminaison standard</span><span class="sxs-lookup"><span data-stu-id="6b700-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="6b700-129">Les points de terminaison standard peuvent être ajoutés dans le code ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="6b700-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="6b700-130">Pour ajouter un point de terminaison standard dans le code, il suffit d'instancier le type de point de terminaison standard approprié et de l'ajouter à l'hôte de service, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6b700-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="6b700-131">Pour ajouter un point de terminaison standard `endpoint` dans la configuration, ajoutez un `service` élément <> à l’élément <`standardEndpoints`> et aux paramètres de configuration nécessaires dans l’élément <>.</span><span class="sxs-lookup"><span data-stu-id="6b700-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="6b700-132">L'exemple suivant montre comment ajouter un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, l'un des points de terminaison standard fournis avec [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b700-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="6b700-133">Le type de critère standard est spécifié à l’aide de l’attribut type dans l’élément `endpoint` <>.</span><span class="sxs-lookup"><span data-stu-id="6b700-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="6b700-134">Le point de terminaison est `standardEndpoints` configuré dans l’élément> <.</span><span class="sxs-lookup"><span data-stu-id="6b700-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="6b700-135">Dans l'exemple ci-dessus, un point de terminaison <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est ajouté et configuré.</span><span class="sxs-lookup"><span data-stu-id="6b700-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="6b700-136">L’élément `udpDiscoveryEndpoint`> <contient un `standardEndpoint`> <qui définit <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> la propriété <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>de la .</span><span class="sxs-lookup"><span data-stu-id="6b700-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="6b700-137">Points de terminaison standard fournis avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6b700-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="6b700-138">Le tableau suivant répertorie les points de terminaison standard fournis avec le [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b700-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="6b700-139">Point de terminaison standard utilisé pour exposer des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="6b700-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="6b700-140">Point de terminaison standard utilisé par les services pour envoyer des messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="6b700-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="6b700-141">Point de terminaison standard utilisé par les services pour envoyer des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="6b700-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="6b700-142">Point de terminaison standard préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="6b700-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="6b700-143">Point de terminaison standard utilisé par les services pour envoyer des messages d’annonce sur une liaison UDP.</span><span class="sxs-lookup"><span data-stu-id="6b700-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="6b700-144">Point de terminaison standard qui utilise WS-Discovery pour rechercher l'adresse du point de terminaison dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6b700-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="6b700-145">Point de terminaison standard pour l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6b700-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="6b700-146">Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding> qui ajoute automatiquement le comportement <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6b700-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="6b700-147">Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding> qui ajoute automatiquement le comportement <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6b700-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="6b700-148">Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6b700-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="6b700-149">Point de terminaison standard qui vous permet d'appeler des opérations de contrôle sur les instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="6b700-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="6b700-150">Point de terminaison standard qui prend en charge la création de workflow et la reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="6b700-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
