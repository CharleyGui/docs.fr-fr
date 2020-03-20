---
title: Exemple Configuration
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 5ac72db1fce0862381cd614499b5db4b9d95b2d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183913"
---
# <a name="configuration-sample"></a>Exemple Configuration
Cet exemple illustre l'utilisation d'un fichier de configuration pour rendre un service détectable.  
  
> [!NOTE]
> Cet exemple implémente la découverte dans la configuration. Pour un échantillon qui implémente la découverte dans le code, voir [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Configuration du service  
 Le fichier de configuration de cet exemple illustre deux fonctionnalités :  
  
- rendre le service détectable sur un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard ;  
  
- ajuster les informations relatives à la découverte pour le point de terminaison d'application du service et ajuster certains paramètres liés à découverte sur le point de terminaison standard.  
  
 Pour activer la découverte, quelques modifications doivent être apportées au fichier de configuration de l'application pour le service :  
  
- Un point de terminaison de découverte doit être ajouté à l'élément `<service>`. Il s'agit d'un point de terminaison <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard. Ce point de terminaison système est associé au service de découverte par le runtime. Le service de découverte écoute les messages sur ce point de terminaison.  
  
- Un comportement `<serviceDiscovery>` est ajouté à la section `<serviceBehaviors>`. Ainsi, le service peut être découvert au moment de l'exécution et utilise le point de terminaison de découverte mentionné précédemment pour écouter les messages de découverte `Probe` et `Resolve`. Grâce à ces deux ajouts, le service est détectable au point de terminaison de découverte spécifié.  
  
 L'extrait de configuration suivant affiche un service avec un point de terminaison d'application et un point de terminaison de découverte définis :  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"
                    kind="udpDiscoveryEndpoint"
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 Pour tirer parti des annonces, vous devez ajouter un point de terminaison d'annonce. Pour cela, modifiez le fichier de configuration comme indiqué dans le code suivant.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 L'ajout d'un point de terminaison d'annonce au comportement du service de découverte crée un client d'annonce par défaut pour le service. Cela garantit que le service va envoyer une annonce en ligne et hors ligne selon qu'il est respectivement ouvert ou fermé.  
  
 Ce fichier de configuration va au delà de ces simples étapes en modifiant des comportements supplémentaires. Il est possible de contrôler les informations relatives à la découverte à l'aide de points de terminaison spécifiques. Autrement dit, un utilisateur peut contrôler si un point de terminaison peut être découvert et marquer ce point de terminaison avec <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> et des métadonnées XML personnalisées. Pour cela, l'utilisateur doit ajouter une propriété `behaviorConfiguration` au point de terminaison d'application. Dans ce cas, la propriété suivante est ajoutée au point de terminaison d'application.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Vous pouvez à présent, via l'élément de configuration de comportement, contrôler les attributs relatifs à la découverte. Dans ce cas, deux portées sont ajoutées au point de terminaison d'application.  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
```  
  
 Pour plus d’informations sur les portées, voir [Discovery Find et FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Vous pouvez également contrôler des détails spécifiques du point de terminaison de découverte. Cette opération s'effectue via le <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. Dans cet exemple, la version du protocole utilisée est modifiée et un attribut `maxResponseDelay` est ajouté, comme le montre l'exemple de code suivant.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 L'exemple qui suit correspond au fichier de configuration complet utilisé dans cet exemple :  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a>Configuration client  
 Le fichier de configuration de l'application pour le client utilise un `standardEndpoint` de type `dynamicEndpoint` afin d'utiliser la découverte, comme indiqué dans l'extrait de configuration suivant.  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 Lorsqu'un client utilise un `dynamicEndpoint`, le runtime effectue automatiquement la découverte. Différents paramètres sont utilisés pendant la découverte, comme ceux définis dans la section `discoveryClientSettings`, qui spécifie le type de point de terminaison de découverte à utiliser :  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Pour connaître les critères utilisés pour rechercher des services :  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 Cet exemple étend cette fonctionnalité et modifie le <xref:System.ServiceModel.Discovery.FindCriteria> utilisé par le client, ainsi que certaines propriétés de l’`updDiscoveryEndpoint` standard utilisé pour la découverte. Les critères <xref:System.ServiceModel.Discovery.FindCriteria> sont modifiés de façon à utiliser une portée et un algorithme `scopeMatchBy` spécifiques, ainsi que des critères d'arrêt personnalisés. En outre, l'exemple montre également comment un client peut envoyer des éléments XML à l'aide de messages `Probe`. Enfin, certaines modifications sont apportées au <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, comme la version du protocole utilisée et des paramètres propres au protocole UDP, ainsi que le montre le fichier de configuration suivant.  
  
```xml  
<udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
```  
  
 L'exemple qui suit correspond à la configuration complète du client utilisée dans l'exemple.  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées. Pour plus d’informations, voir [Configuring HTTP et HTTPS](../feature-details/configuring-http-and-https.md). L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées. Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Générez la solution.  
  
3. Exécutez le fichier exécutable du service à partir du répertoire de build.  
  
4. Exécutez le fichier exécutable du client. Notez que le client est en mesure de trouver le service.  
