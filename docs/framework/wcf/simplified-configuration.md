---
title: Configuration simplifiée
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 5aaca8ae8c456e2377326ee2e9e22c3dcf6a21a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922999"
---
# <a name="simplified-configuration"></a><span data-ttu-id="8d0ac-102">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="8d0ac-102">Simplified Configuration</span></span>
<span data-ttu-id="8d0ac-103">La configuration des services de Windows Communication Foundation (WCF) peut être une tâche complexe.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="8d0ac-104">Il existe de nombreuses options différentes et il n'est pas toujours évident de déterminer les paramètres nécessaires.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="8d0ac-105">Alors que les fichiers de configuration augmentent la flexibilité des services WCF, ils sont également la source de nombreux problèmes difficiles à détecter.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="8d0ac-106">traite ces problèmes et permet de réduire la taille et la complexité de la configuration de service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="8d0ac-107">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="8d0ac-107">Simplified Configuration</span></span>  
 <span data-ttu-id="8d0ac-108">Dans les fichiers de configuration du service WCF`system.serviceModel`, la section > <`service`contient un élément < > pour chaque service hébergé.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="8d0ac-109">L’élément`service`< > contient une collection d’éléments`endpoint`< > qui spécifient les points de terminaison exposés pour chaque service et éventuellement un ensemble de comportements de service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="8d0ac-110">Les éléments`endpoint`de > < spécifient l’adresse, la liaison et le contrat exposés par le point de terminaison, et éventuellement la liaison des comportements de configuration et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="8d0ac-111">La section`system.serviceModel`> < contient également un élément`behaviors`< > qui vous permet de spécifier des comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="8d0ac-112">L’exemple suivant montre le <`system.serviceModel`> section d’un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="8d0ac-113">facilite la configuration d’un service WCF en supprimant la nécessité de l'`service`élément < >.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="8d0ac-114">Si vous n’ajoutez pas de <`service`section > ou si vous ajoutez des points de terminaison`service`dans une section de > < et que votre service ne définit aucun point de terminaison par programmation, un jeu de points de terminaison par défaut est automatiquement ajouté à votre service, un pour chaque adresse de base du service et pour chaque contrat implémenté par votre service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="8d0ac-115">Dans chacun de ces points de terminaison, l’adresse du point de terminaison correspond à l’adresse de base, la liaison est déterminée par le schéma d’adresse de base et le contrat est celui implémenté par votre service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="8d0ac-116">Si vous n’avez pas besoin de spécifier de comportements de point de terminaison ou de service, ni de modifier un paramètre de liaison, il est inutile de spécifier un fichier de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="8d0ac-117">Si un service implémente deux contrats et que l'hôte active à la fois les transports HTTP et TCP, l'hôte de service crée quatre points de terminaison par défaut, un pour chaque contrat utilisant chaque transport.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="8d0ac-118">Pour créer des points de terminaison par défaut, l'hôte de service doit savoir quelles liaisons utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="8d0ac-119">Ces paramètres sont spécifiés dans une`protocolMappings`section > < dans la`system.serviceModel`section > de <.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="8d0ac-120">La section`protocolMappings`> < contient une liste de schémas de protocole de transport mappés aux types de liaison.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="8d0ac-121">L’hôte du service utilise les adresses de base qui lui sont transmises pour déterminer quelle liaison utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="8d0ac-122">L’exemple suivant utilise l’élément`protocolMappings`< >.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8d0ac-123">Le fait de modifier les éléments de configuration par défaut, comme les liaisons ou les comportements, peut affecter les services définis dans les niveaux inférieurs de la hiérarchie de configuration, car ces derniers peuvent utiliser ces liaisons et comportements par défaut.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="8d0ac-124">C’est pourquoi, la personne qui modifie les liaisons et comportements par défaut doit savoir que ces changements peuvent affecter d’autres services dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d0ac-125">Les services hébergés dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service) utilisent le répertoire virtuel comme leur adresse de base.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="8d0ac-126">Dans l'exemple précédent, un point de terminaison avec une adresse de base commençant par le schéma « http » utilise la liaison <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="8d0ac-127">Un point de terminaison avec une adresse de base commençant par le schéma « net.tcp » utilise la liaison <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="8d0ac-128">Vous pouvez remplacer des paramètres dans un fichier local App.config ou Web.config.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="8d0ac-129">Chaque élément de la section`protocolMappings`> < doit spécifier un schéma et une liaison.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="8d0ac-130">Éventuellement, il peut spécifier un `bindingConfiguration` attribut qui spécifie une configuration de liaison dans`bindings`la section < > du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="8d0ac-131">Si aucun attribut `bindingConfiguration` n’est spécifié, la configuration de liaison anonyme du type de liaison approprié est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="8d0ac-132">Les comportements de service sont configurés pour les points de terminaison par défaut`behavior`à l’aide de`serviceBehaviors`< anonymes > sections dans < sections de >.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="8d0ac-133">Les éléments <`behavior`> sans nom dans <`serviceBehaviors`> sont utilisés pour configurer les comportements de service.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="8d0ac-134">Par exemple, le fichier de configuration suivant permet la publication de métadonnées de service pour tous les services qui se trouvent dans l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="8d0ac-135">Les comportements de point de terminaison sont configurés`behavior`à l’aide des`serviceBehaviors`sections anonymes < > dans < > sections.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="8d0ac-136">L'exemple suivant est un fichier de configuration équivalent à celui qui se trouve au début de cette rubrique. Il utilise le modèle de configuration simplifié.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> <span data-ttu-id="8d0ac-137">Cette fonctionnalité concerne uniquement la configuration du service WCF, non la configuration du client.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="8d0ac-138">La plupart de temps, la configuration cliente WCF est générée par un outil comme svcutil.exe ou en ajoutant une référence de service à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="8d0ac-139">Si vous configurez manuellement un client WCF, vous devez ajouter un \<élément client > à la configuration et spécifier tous les points de terminaison que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="8d0ac-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0ac-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d0ac-140">See also</span></span>

- [<span data-ttu-id="8d0ac-141">Configuration des services à l’aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8d0ac-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="8d0ac-142">Configuration de liaisons pour les services</span><span class="sxs-lookup"><span data-stu-id="8d0ac-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="8d0ac-143">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="8d0ac-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8d0ac-144">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="8d0ac-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="8d0ac-145">Configuration des services WCF</span><span class="sxs-lookup"><span data-stu-id="8d0ac-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="8d0ac-146">Configuration des services WCF dans le code</span><span class="sxs-lookup"><span data-stu-id="8d0ac-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
