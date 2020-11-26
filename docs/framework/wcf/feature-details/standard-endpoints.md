---
title: Points de terminaison standard
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: a2f8d45990c5bc845aeee87ee82a2d043d6d1292
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246444"
---
# <a name="standard-endpoints"></a>Points de terminaison standard

Les points de terminaison sont définis en spécifiant une adresse, une liaison et un contrat. Les autres paramètres qui peuvent être définis sur un point de terminaison incluent la configuration du comportement, les en-têtes, et les URI d'écoute.  Pour certains types de points de terminaison, ces valeurs ne changent pas. Par exemple, les points de terminaison d'échange de métadonnées utilisent toujours le contrat <xref:System.ServiceModel.Description.IMetadataExchange>. D'autres points de terminaison, tels que <xref:System.ServiceModel.Description.WebHttpEndpoint>, requièrent toujours un comportement de point de terminaison spécifié. L'utilisation d'un point de terminaison peut être simplifiée par l'emploi de points de terminaison possédant des valeurs par défaut pour des propriétés de point de terminaison courantes. Les points de terminaison standard permettent à un développeur de définir un point de terminaison avec des valeurs par défaut ou dont une ou plusieurs propriétés de point de terminaison restent inchangées.  Les points de terminaison de ce type vous permettent d'utiliser un point de terminaison sans avoir à spécifier les informations qui sont de nature statique. Les points de terminaison standard peuvent être utilisés comme points de terminaison d'infrastructure et d'application.  
  
## <a name="infrastructure-endpoints"></a>Points de terminaison d'infrastructure  

 Un service peut exposer des points de terminaison dont certaines des propriétés n'ont pas été implémentées de manière explicite par l'auteur du service. Par exemple, le point de terminaison d'échange de métadonnées expose le contrat <xref:System.ServiceModel.Description.IMetadataExchange>, mais vous n'implémentez pas cette interface en tant qu'auteur du service, elle est implémentée par WCF. Ces points de terminaison d'infrastructure ont des valeurs par défaut pour une ou plusieurs propriétés de point de terminaison, dont certaines peuvent être immuables. La propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> du point de terminaison d'échange de métadonnées doit être <xref:System.ServiceModel.Description.IMetadataExchange>, tandis que d'autres propriétés comme la liaison peuvent être fournies par le développeur. Les points de terminaison d'infrastructure sont identifiés en attribuant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> la valeur `true`.  
  
## <a name="application-endpoints"></a>Points de terminaison d'application  

 Les développeurs d’applications peuvent définir leurs propres points de terminaison standard qui spécifient des valeurs par défaut pour l’adresse, la liaison ou le contrat. Vous définissez un point de terminaison standard en dérivant une classe de <xref:System.ServiceModel.Description.ServiceEndpoint> et en définissant les propriétés de point de terminaison appropriées. Vous pouvez fournir des valeurs par défaut pour les propriétés qui peuvent être modifiées. D'autres propriétés ont des valeurs statiques qui ne peuvent pas être modifiées. L'exemple suivant indique comment implémenter un point de terminaison standard.  
  
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
  
 Pour utiliser un point de terminaison personnalisé défini par l’utilisateur dans un fichier de configuration, vous devez dériver une classe de <xref:System.ServiceModel.Configuration.StandardEndpointElement> , dériver une classe de <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> et enregistrer le nouveau point de terminaison standard dans la section extensions de app.config ou machine.config.  Le <xref:System.ServiceModel.Configuration.StandardEndpointElement> fournit la prise en charge de la configuration pour le point de terminaison standard, comme illustré dans l’exemple suivant.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>Fournit le type de stockage pour la collection qui s’affiche sous la `standardEndpoints` section <> dans la configuration du point de terminaison standard.  L'exemple suivant montre comment implémenter cette classe.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

L’exemple suivant montre comment enregistrer un point de terminaison standard dans la section des extensions.

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
  
## <a name="configuring-a-standard-endpoint"></a>Configuration d'un point de terminaison standard  

 Les points de terminaison standard peuvent être ajoutés dans le code ou dans la configuration.  Pour ajouter un point de terminaison standard dans le code, il suffit d'instancier le type de point de terminaison standard approprié et de l'ajouter à l'hôte de service, comme indiqué dans l'exemple suivant :  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Pour ajouter un point de terminaison standard dans la configuration, ajoutez un `endpoint` élément <> au <`service` élément> et les paramètres de configuration nécessaires dans l' `standardEndpoints` élément <>. L'exemple suivant montre comment ajouter un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, l'un des points de terminaison standard fournis avec [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Le type de point de terminaison standard est spécifié à l’aide de l’attribut kind dans l' `endpoint` élément <>. Le point de terminaison est configuré dans l' `standardEndpoints` élément <>. Dans l'exemple ci-dessus, un point de terminaison <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est ajouté et configuré. L' `udpDiscoveryEndpoint` élément <> contient une `standardEndpoint`> <qui définit la <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> propriété de <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Points de terminaison standard fournis avec le .NET Framework  

 Le tableau suivant répertorie les points de terminaison standard fournis avec le [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Point de terminaison standard utilisé pour exposer des métadonnées de service.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Point de terminaison standard utilisé par les services pour envoyer des messages d'annonce.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Point de terminaison standard utilisé par les services pour envoyer des messages de découverte.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Point de terminaison standard préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Point de terminaison standard utilisé par les services pour envoyer des messages d’annonce sur une liaison UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Point de terminaison standard qui utilise WS-Discovery pour rechercher l'adresse du point de terminaison dynamiquement au moment de l'exécution.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Point de terminaison standard pour l'échange de métadonnées.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding> qui ajoute automatiquement le comportement <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding> qui ajoute automatiquement le comportement <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Point de terminaison standard avec une liaison <xref:System.ServiceModel.WebHttpBinding>.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Point de terminaison standard qui vous permet d'appeler des opérations de contrôle sur les instances de workflow.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Point de terminaison standard qui prend en charge la création de workflow et la reprise de signet.
