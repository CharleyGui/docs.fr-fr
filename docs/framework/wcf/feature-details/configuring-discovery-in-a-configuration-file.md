---
title: Configuration de la découverte dans un fichier de configuration
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 1ffd5cb2e884b6eeae292326cb0dc1586995ba38
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284184"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="36d36-102">Configuration de la découverte dans un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="36d36-102">Configuring Discovery in a Configuration File</span></span>

<span data-ttu-id="36d36-103">Il existe quatre principaux groupes de paramètres de configuration utilisés dans la découverte.</span><span class="sxs-lookup"><span data-stu-id="36d36-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="36d36-104">Cette rubrique décrit brièvement chaque groupe et montre des exemples de configuration.</span><span class="sxs-lookup"><span data-stu-id="36d36-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="36d36-105">À la suite de chaque section, un lien vous permettra d'accéder à des informations détaillées sur chaque zone.</span><span class="sxs-lookup"><span data-stu-id="36d36-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="36d36-106">Configuration de comportements</span><span class="sxs-lookup"><span data-stu-id="36d36-106">Behavior Configuration</span></span>  

 <span data-ttu-id="36d36-107">La découverte utilise des comportements de service et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="36d36-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="36d36-108">Le comportement <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> active la découverte pour tous les points de terminaison d'un service et vous permet de spécifier des points de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="36d36-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="36d36-109">L'exemple suivant indique comment ajouter le comportement <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> et spécifier un point de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="36d36-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="36d36-110">Une fois que vous avez spécifié le comportement, référencez-le à partir d’un `service` élément <> comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="36d36-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </services>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="36d36-111">Pour qu'un service soit détectable, vous devez également ajouter un point de terminaison de découverte ; l'exemple ci-dessus ajoute un point de terminaison standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="36d36-112">Lorsque vous ajoutez des points de terminaison d’annonce, vous devez également ajouter un service d’écoute de l’annonce à l' `services` élément <> comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="36d36-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>
```  
  
 <span data-ttu-id="36d36-113">Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est utilisé pour activer ou désactiver la découverte d'un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="36d36-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="36d36-114">L'exemple suivant configure un service avec deux points de terminaison d'application, un avec la découverte activée et l'autre avec la découverte désactivée.</span><span class="sxs-lookup"><span data-stu-id="36d36-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="36d36-115">Pour chaque point de terminaison un comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est ajouté.</span><span class="sxs-lookup"><span data-stu-id="36d36-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
   <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="36d36-116">Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> peut également être utilisé pour ajouter des métadonnées personnalisées aux métadonnées de point de terminaison retournées par le service.</span><span class="sxs-lookup"><span data-stu-id="36d36-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="36d36-117">L’exemple suivant vous montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="36d36-117">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="36d36-118">Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> peut également être utilisé pour ajouter des étendues et des types utilisés par les clients pour rechercher des services.</span><span class="sxs-lookup"><span data-stu-id="36d36-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="36d36-119">L'exemple suivant indique comment les ajouter dans un fichier de configuration côté client.</span><span class="sxs-lookup"><span data-stu-id="36d36-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="36d36-120">Pour plus d’informations sur <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> et <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> consultez [vue d’ensemble de la découverte WCF](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36d36-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="36d36-121">Configuration d’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="36d36-121">Binding Element Configuration</span></span>  

 <span data-ttu-id="36d36-122">La configuration d’élément de liaison est très intéressante sur le côté client.</span><span class="sxs-lookup"><span data-stu-id="36d36-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="36d36-123">Vous pouvez utiliser la configuration pour spécifier les critères de recherche utilisés pour découvrir les services d'une application cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="36d36-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="36d36-124">L’exemple suivant crée une liaison personnalisée avec le canal <xref:System.ServiceModel.Discovery.DiscoveryClient> et spécifie des critères de recherche qui incluent un type et une étendue.</span><span class="sxs-lookup"><span data-stu-id="36d36-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="36d36-125">En outre, il spécifie les valeurs des propriétés <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> et <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>.</span><span class="sxs-lookup"><span data-stu-id="36d36-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
      </binding>
   </customBinding>
</bindings>  
```  
  
 <span data-ttu-id="36d36-126">Cette configuration de liaison personnalisée doit être référencée par un point de terminaison client :</span><span class="sxs-lookup"><span data-stu-id="36d36-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="36d36-127">Pour plus d’informations sur les critères de recherche [, consultez recherche de découverte et FindCriteria](discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="36d36-127">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="36d36-128">Pour plus d’informations sur la découverte et les éléments de liaison, consultez [vue d’ensemble de la découverte WCF](wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="36d36-128">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="36d36-129">Configuration de point de terminaison standard</span><span class="sxs-lookup"><span data-stu-id="36d36-129">Standard Endpoint Configuration</span></span>  

 <span data-ttu-id="36d36-130">Les points de terminaison standard sont des points de terminaison prédéfinis qui ont des valeurs par défaut pour une ou plusieurs propriétés (adresse, liaison ou contrat) ou une ou plusieurs valeurs de propriété qui ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="36d36-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="36d36-131">Le .NET 4 est fourni avec 3 points de terminaison standard liés à la découverte : <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> et <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="36d36-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est un point de terminaison standard, préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="36d36-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="36d36-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> est un point de terminaison standard, préconfiguré pour envoyer des messages d'annonce sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="36d36-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="36d36-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> est un point de terminaison standard qui utilise la découverte pour rechercher l'adresse du point de terminaison d'un service découvert de manière dynamique, au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="36d36-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="36d36-135">Les liaisons standard sont spécifiées avec un `endpoint` élément <> contenant l’attribut Kind qui a spécifié le type de point de terminaison standard à ajouter.</span><span class="sxs-lookup"><span data-stu-id="36d36-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="36d36-136">L'exemple suivant montre comment ajouter un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> dans un <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="36d36-137">Les points de terminaison standard sont configurés dans un `standardEndpoints` élément <>.</span><span class="sxs-lookup"><span data-stu-id="36d36-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="36d36-138">L'exemple suivant montre comment configurer les points de terminaison standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> et <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint
            name="udpAnnouncementEndpointSettings"
            multicastAddress="soap.udp://239.255.255.250:3703"
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="36d36-139">Une fois que vous avez ajouté la configuration du point de terminaison standard, référencez la configuration dans l' `endpoint` élément <> pour chaque point de terminaison, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="36d36-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="36d36-140">Contrairement aux autres points de terminaison standard utilisés dans la découverte, vous spécifiez une liaison et un contrat pour <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="36d36-141">L'exemple suivant montre comment ajouter et configurer un point de terminaison standard <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="36d36-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="36d36-142">Pour plus d’informations sur les points de terminaison standard, consultez [points de terminaison standard](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="36d36-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
