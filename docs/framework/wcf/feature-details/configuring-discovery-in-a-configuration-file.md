---
title: Configuration de la découverte dans un fichier de configuration
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 934b04b51b9954cf943f57f33250951048e5671b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464207"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Configuration de la découverte dans un fichier de configuration
Il existe quatre principaux groupes de paramètres de configuration utilisés dans la découverte. Cette rubrique décrit brièvement chaque groupe et montre des exemples de configuration. À la suite de chaque section, un lien vous permettra d'accéder à des informations détaillées sur chaque zone.  
  
## <a name="behavior-configuration"></a>Configuration de comportements  
 La découverte utilise des comportements de service et de point de terminaison. Le comportement <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> active la découverte pour tous les points de terminaison d'un service et vous permet de spécifier des points de terminaison d'annonce.  L'exemple suivant indique comment ajouter le comportement <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> et spécifier un point de terminaison d'annonce.  
  
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
  
 Une fois que vous spécifiez `service` le comportement, référencez-le à partir d’un élément> <tel qu’indiqué dans l’échantillon suivant.  
  
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
  
 Pour qu'un service soit détectable, vous devez également ajouter un point de terminaison de découverte ; l'exemple ci-dessus ajoute un point de terminaison standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
 Lorsque vous ajoutez des paramètres d’annonce, vous devez également ajouter `services` un service d’écoute d’annonce à l'<> élément tel que indiqué dans l’exemple suivant.  
  
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
  
 Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est utilisé pour activer ou désactiver la découverte d'un point de terminaison spécifique.  L'exemple suivant configure un service avec deux points de terminaison d'application, un avec la découverte activée et l'autre avec la découverte désactivée. Pour chaque point de terminaison un comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est ajouté.  
  
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
  
 Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> peut également être utilisé pour ajouter des métadonnées personnalisées aux métadonnées de point de terminaison retournées par le service. L’exemple suivant vous montre comment procéder.  
  
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
  
 Le comportement <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> peut également être utilisé pour ajouter des étendues et des types utilisés par les clients pour rechercher des services. L'exemple suivant indique comment les ajouter dans un fichier de configuration côté client.  
  
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
  
 Pour plus <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> d’informations sur et <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> voir [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Configuration d’élément de liaison.  
 La configuration d’élément de liaison est très intéressante sur le côté client. Vous pouvez utiliser la configuration pour spécifier les critères de recherche utilisés pour découvrir les services d'une application cliente WCF.  L’exemple suivant crée une liaison personnalisée avec le canal <xref:System.ServiceModel.Discovery.DiscoveryClient> et spécifie des critères de recherche qui incluent un type et une étendue. En outre, il spécifie les valeurs des propriétés <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> et <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>.  
  
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
  
 Cette configuration de liaison personnalisée doit être référencée par un point de terminaison client :  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Pour plus d’informations sur les critères de recherche voir [Discovery Find et FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Pour plus d’informations sur la découverte et les éléments contraignants voir, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Configuration de point de terminaison standard  
 Les points de terminaison standard sont des points de terminaison prédéfinis qui ont des valeurs par défaut pour une ou plusieurs propriétés (adresse, liaison ou contrat) ou une ou plusieurs valeurs de propriété qui ne peuvent pas être modifiées. Le .NET 4 est fourni avec 3 points de terminaison standard liés à la découverte : <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> et <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est un point de terminaison standard, préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> est un point de terminaison standard, préconfiguré pour envoyer des messages d'annonce sur une liaison de multidiffusion UDP. <xref:System.ServiceModel.Discovery.DynamicEndpoint> est un point de terminaison standard qui utilise la découverte pour rechercher l'adresse du point de terminaison d'un service découvert de manière dynamique, au moment de l'exécution.  Les fixations standard sont spécifiées `endpoint` avec un élément <> qui contient un attribut type qui précisait le type de critère d’évaluation standard à ajouter. L'exemple suivant montre comment ajouter un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> dans un <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Les paramètres standard sont configurés `standardEndpoints` dans un élément <>. L'exemple suivant montre comment configurer les points de terminaison standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> et <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Une fois que vous avez ajouté la configuration standard du `endpoint` point de terminaison, faites référence à la configuration dans le <> élément pour chaque point de terminaison tel qu’indiqué dans l’échantillon suivant.  
  
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
  
 Contrairement aux autres points de terminaison standard utilisés dans la découverte, vous spécifiez une liaison et un contrat pour <xref:System.ServiceModel.Discovery.DynamicEndpoint>. L'exemple suivant montre comment ajouter et configurer un point de terminaison standard <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Pour plus d’informations sur les paramètres standard, voir [Standard Endpoints](standard-endpoints.md).
