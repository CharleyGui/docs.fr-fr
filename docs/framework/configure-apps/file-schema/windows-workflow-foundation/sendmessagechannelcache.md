---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: e4f77e95cbacc2d025b57dceed5b1bd0d2851e81
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422899"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="022e8-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="022e8-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="022e8-102">Comportement de service qui permet de personnaliser le partage du cache niveaux, les paramètres de cache de fabrication de canal et les paramètres du cache de canal pour les workflows qui envoient des messages aux points de terminaison de service à l’aide des activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="022e8-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="022e8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="022e8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="022e8-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="022e8-104">\<behaviors></span></span>  
<span data-ttu-id="022e8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="022e8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="022e8-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="022e8-106">\<behavior></span></span>  
<span data-ttu-id="022e8-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="022e8-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022e8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="022e8-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="022e8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="022e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="022e8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="022e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="022e8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="022e8-111">Attributes</span></span>  
  
|<span data-ttu-id="022e8-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="022e8-112">Attribute</span></span>|<span data-ttu-id="022e8-113">Description</span><span class="sxs-lookup"><span data-stu-id="022e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="022e8-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="022e8-114">allowUnsafeCaching</span></span>|<span data-ttu-id="022e8-115">Valeur booléenne qui indique s'il faut activer la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="022e8-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="022e8-116">Si le service de flux de travail comporte des liaisons ou des comportements personnalisés, la mise en cache pourrait être non sécurisée et donc désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="022e8-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="022e8-117">Toutefois, si vous voulez activer la mise en cache affectez à cette propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="022e8-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="022e8-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="022e8-118">Child Elements</span></span>  
  
|<span data-ttu-id="022e8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="022e8-119">Element</span></span>|<span data-ttu-id="022e8-120">Description</span><span class="sxs-lookup"><span data-stu-id="022e8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="022e8-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="022e8-121">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="022e8-122">Spécifie les paramètres du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="022e8-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="022e8-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="022e8-123">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="022e8-124">Spécifie les paramètres du cache de la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="022e8-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="022e8-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="022e8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="022e8-126">Élément</span><span class="sxs-lookup"><span data-stu-id="022e8-126">Element</span></span>|<span data-ttu-id="022e8-127">Description</span><span class="sxs-lookup"><span data-stu-id="022e8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="022e8-128">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="022e8-128">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="022e8-129">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="022e8-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="022e8-130">Notes</span><span class="sxs-lookup"><span data-stu-id="022e8-130">Remarks</span></span>  
 <span data-ttu-id="022e8-131">Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="022e8-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="022e8-132">Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="022e8-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="022e8-133">Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="022e8-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="022e8-134">Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance).</span><span class="sxs-lookup"><span data-stu-id="022e8-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="022e8-135">La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="022e8-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="022e8-136">Pour plus d’informations sur la modification des paramètres de cache pour la fabrication de canal et le cache de canaux et niveaux de partage de cache par défaut, consultez [changement des niveaux de partage de Cache pour les activités d’envoi](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="022e8-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="022e8-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="022e8-137">Example</span></span>  
 <span data-ttu-id="022e8-138">Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="022e8-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="022e8-139">Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service.</span><span class="sxs-lookup"><span data-stu-id="022e8-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="022e8-140">L’exemple suivant montre le contenu d’un fichier de configuration qui contient le `MyChannelCacheBehavior` comportement de service avec les paramètres du cache du cache et le canal de fabrique personnalisée.</span><span class="sxs-lookup"><span data-stu-id="022e8-140">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="022e8-141">Ce comportement de service est ajouté au service via le `behaviorConfiguration` attribut.</span><span class="sxs-lookup"><span data-stu-id="022e8-141">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="022e8-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="022e8-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="022e8-143">Modification des niveaux de partage du cache pour les activités d’envoi</span><span class="sxs-lookup"><span data-stu-id="022e8-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
