---
title: Exemple Configuration
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 6d84085d06da117ebf13fa4bb714513aacc3abd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594723"
---
# <a name="configuration-sample"></a><span data-ttu-id="a43fe-102">Exemple Configuration</span><span class="sxs-lookup"><span data-stu-id="a43fe-102">Configuration Sample</span></span>
<span data-ttu-id="a43fe-103">Cet exemple illustre l'utilisation d'un fichier de configuration pour rendre un service détectable.</span><span class="sxs-lookup"><span data-stu-id="a43fe-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a43fe-104">Cet exemple implémente la découverte dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a43fe-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="a43fe-105">Pour obtenir un exemple qui implémente la découverte dans le code, consultez [Basic](basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a43fe-105">For a sample that implements discovery in code, see [Basic](basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a43fe-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a43fe-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a43fe-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a43fe-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a43fe-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a43fe-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a43fe-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a43fe-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="a43fe-110">Configuration du service</span><span class="sxs-lookup"><span data-stu-id="a43fe-110">Service Configuration</span></span>  
 <span data-ttu-id="a43fe-111">Le fichier de configuration de cet exemple illustre deux fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="a43fe-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="a43fe-112">rendre le service détectable sur un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard ;</span><span class="sxs-lookup"><span data-stu-id="a43fe-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="a43fe-113">ajuster les informations relatives à la découverte pour le point de terminaison d'application du service et ajuster certains paramètres liés à découverte sur le point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="a43fe-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="a43fe-114">Pour activer la découverte, quelques modifications doivent être apportées au fichier de configuration de l'application pour le service :</span><span class="sxs-lookup"><span data-stu-id="a43fe-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="a43fe-115">Un point de terminaison de découverte doit être ajouté à l'élément `<service>`.</span><span class="sxs-lookup"><span data-stu-id="a43fe-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="a43fe-116">Il s'agit d'un point de terminaison <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard.</span><span class="sxs-lookup"><span data-stu-id="a43fe-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="a43fe-117">Ce point de terminaison système est associé au service de découverte par le runtime.</span><span class="sxs-lookup"><span data-stu-id="a43fe-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="a43fe-118">Le service de découverte écoute les messages sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a43fe-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="a43fe-119">Un comportement `<serviceDiscovery>` est ajouté à la section `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="a43fe-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="a43fe-120">Ainsi, le service peut être découvert au moment de l'exécution et utilise le point de terminaison de découverte mentionné précédemment pour écouter les messages de découverte `Probe` et `Resolve`.</span><span class="sxs-lookup"><span data-stu-id="a43fe-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="a43fe-121">Grâce à ces deux ajouts, le service est détectable au point de terminaison de découverte spécifié.</span><span class="sxs-lookup"><span data-stu-id="a43fe-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="a43fe-122">L'extrait de configuration suivant affiche un service avec un point de terminaison d'application et un point de terminaison de découverte définis :</span><span class="sxs-lookup"><span data-stu-id="a43fe-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="a43fe-123">Pour tirer parti des annonces, vous devez ajouter un point de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="a43fe-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="a43fe-124">Pour cela, modifiez le fichier de configuration comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a43fe-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="a43fe-125">L'ajout d'un point de terminaison d'annonce au comportement du service de découverte crée un client d'annonce par défaut pour le service.</span><span class="sxs-lookup"><span data-stu-id="a43fe-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="a43fe-126">Cela garantit que le service va envoyer une annonce en ligne et hors ligne selon qu'il est respectivement ouvert ou fermé.</span><span class="sxs-lookup"><span data-stu-id="a43fe-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="a43fe-127">Ce fichier de configuration va au delà de ces simples étapes en modifiant des comportements supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="a43fe-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="a43fe-128">Il est possible de contrôler les informations relatives à la découverte à l'aide de points de terminaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a43fe-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="a43fe-129">Autrement dit, un utilisateur peut contrôler si un point de terminaison peut être découvert et marquer ce point de terminaison avec <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> et des métadonnées XML personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a43fe-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="a43fe-130">Pour cela, l'utilisateur doit ajouter une propriété `behaviorConfiguration` au point de terminaison d'application.</span><span class="sxs-lookup"><span data-stu-id="a43fe-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="a43fe-131">Dans ce cas, la propriété suivante est ajoutée au point de terminaison d'application.</span><span class="sxs-lookup"><span data-stu-id="a43fe-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="a43fe-132">Vous pouvez à présent, via l'élément de configuration de comportement, contrôler les attributs relatifs à la découverte.</span><span class="sxs-lookup"><span data-stu-id="a43fe-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="a43fe-133">Dans ce cas, deux portées sont ajoutées au point de terminaison d'application.</span><span class="sxs-lookup"><span data-stu-id="a43fe-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="a43fe-134">Pour plus d’informations sur les étendues, consultez [détection de découverte et FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="a43fe-134">For more information about scopes, see [Discovery Find and FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="a43fe-135">Vous pouvez également contrôler des détails spécifiques du point de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="a43fe-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="a43fe-136">Cette opération s'effectue via le <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="a43fe-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="a43fe-137">Dans cet exemple, la version du protocole utilisée est modifiée et un attribut `maxResponseDelay` est ajouté, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a43fe-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="a43fe-138">L'exemple qui suit correspond au fichier de configuration complet utilisé dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="a43fe-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="a43fe-139">Configuration client</span><span class="sxs-lookup"><span data-stu-id="a43fe-139">Client Configuration</span></span>  
 <span data-ttu-id="a43fe-140">Le fichier de configuration de l'application pour le client utilise un `standardEndpoint` de type `dynamicEndpoint` afin d'utiliser la découverte, comme indiqué dans l'extrait de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="a43fe-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="a43fe-141">Lorsqu'un client utilise un `dynamicEndpoint`, le runtime effectue automatiquement la découverte.</span><span class="sxs-lookup"><span data-stu-id="a43fe-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="a43fe-142">Différents paramètres sont utilisés pendant la découverte, comme ceux définis dans la section `discoveryClientSettings`, qui spécifie le type de point de terminaison de découverte à utiliser :</span><span class="sxs-lookup"><span data-stu-id="a43fe-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="a43fe-143">Pour connaître les critères utilisés pour rechercher des services :</span><span class="sxs-lookup"><span data-stu-id="a43fe-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="a43fe-144">Cet exemple étend cette fonctionnalité et modifie le <xref:System.ServiceModel.Discovery.FindCriteria> utilisé par le client, ainsi que certaines propriétés de l’`updDiscoveryEndpoint` standard utilisé pour la découverte.</span><span class="sxs-lookup"><span data-stu-id="a43fe-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="a43fe-145">Les critères <xref:System.ServiceModel.Discovery.FindCriteria> sont modifiés de façon à utiliser une portée et un algorithme `scopeMatchBy` spécifiques, ainsi que des critères d'arrêt personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a43fe-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="a43fe-146">En outre, l'exemple montre également comment un client peut envoyer des éléments XML à l'aide de messages `Probe`.</span><span class="sxs-lookup"><span data-stu-id="a43fe-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="a43fe-147">Enfin, certaines modifications sont apportées au <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, comme la version du protocole utilisée et des paramètres propres au protocole UDP, ainsi que le montre le fichier de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="a43fe-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a43fe-148">L'exemple qui suit correspond à la configuration complète du client utilisée dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a43fe-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
</configuration>
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a43fe-149">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="a43fe-149">To use this sample</span></span>  
  
1. <span data-ttu-id="a43fe-150">Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées.</span><span class="sxs-lookup"><span data-stu-id="a43fe-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="a43fe-151">Pour plus d’informations, consultez [configuration de http et HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="a43fe-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="a43fe-152">L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="a43fe-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="a43fe-153">Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle.</span><span class="sxs-lookup"><span data-stu-id="a43fe-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="a43fe-154">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="a43fe-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="a43fe-155">Exécutez le fichier exécutable du service à partir du répertoire de build.</span><span class="sxs-lookup"><span data-stu-id="a43fe-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="a43fe-156">Exécutez le fichier exécutable du client.</span><span class="sxs-lookup"><span data-stu-id="a43fe-156">Run the client executable.</span></span> <span data-ttu-id="a43fe-157">Notez que le client est en mesure de trouver le service.</span><span class="sxs-lookup"><span data-stu-id="a43fe-157">Note that the client is able to locate the service.</span></span>  
