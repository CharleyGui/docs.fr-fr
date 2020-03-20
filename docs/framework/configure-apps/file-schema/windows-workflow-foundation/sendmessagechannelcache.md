---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151999"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="f4c86-101">\<envoyerMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="f4c86-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="f4c86-102">Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="f4c86-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="f4c86-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4c86-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4c86-104">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f4c86-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f4c86-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportements>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f4c86-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f4c86-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f4c86-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f4c86-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportement>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f4c86-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f4c86-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<envoyerMessageChannelCache>**</span><span class="sxs-lookup"><span data-stu-id="f4c86-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c86-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4c86-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4c86-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4c86-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f4c86-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4c86-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4c86-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4c86-112">Attributes</span></span>  
  
|<span data-ttu-id="f4c86-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f4c86-113">Attribute</span></span>|<span data-ttu-id="f4c86-114">Description</span><span class="sxs-lookup"><span data-stu-id="f4c86-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4c86-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="f4c86-115">allowUnsafeCaching</span></span>|<span data-ttu-id="f4c86-116">Valeur booléenne qui indique s'il faut activer la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="f4c86-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="f4c86-117">Si le service de flux de travail comporte des liaisons ou des comportements personnalisés, la mise en cache pourrait être non sécurisée et donc désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4c86-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="f4c86-118">Cependant, si vous voulez tourner la mise en cache sur le plateau de cette propriété à **vrai**.</span><span class="sxs-lookup"><span data-stu-id="f4c86-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4c86-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4c86-119">Child Elements</span></span>  
  
|<span data-ttu-id="f4c86-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f4c86-120">Element</span></span>|<span data-ttu-id="f4c86-121">Description</span><span class="sxs-lookup"><span data-stu-id="f4c86-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4c86-122">\<canauxSettings></span><span class="sxs-lookup"><span data-stu-id="f4c86-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="f4c86-123">Spécifie les paramètres du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="f4c86-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="f4c86-124">\<usineSettings></span><span class="sxs-lookup"><span data-stu-id="f4c86-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="f4c86-125">Spécifie les paramètres du cache de la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="f4c86-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4c86-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4c86-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f4c86-127">Élément</span><span class="sxs-lookup"><span data-stu-id="f4c86-127">Element</span></span>|<span data-ttu-id="f4c86-128">Description</span><span class="sxs-lookup"><span data-stu-id="f4c86-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4c86-129">\<comportement> de \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f4c86-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f4c86-130">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="f4c86-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4c86-131">Notes </span><span class="sxs-lookup"><span data-stu-id="f4c86-131">Remarks</span></span>  
 <span data-ttu-id="f4c86-132">Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="f4c86-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="f4c86-133">Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f4c86-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="f4c86-134">Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="f4c86-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="f4c86-135">Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance).</span><span class="sxs-lookup"><span data-stu-id="f4c86-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="f4c86-136">La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="f4c86-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="f4c86-137">Pour plus d’informations sur la façon de modifier les niveaux de partage de cache par défaut et les paramètres de cache pour l’usine de canaux et le cache de canal, voir [Changer les niveaux de partage de cache pour envoyer des activités](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f4c86-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c86-138"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f4c86-138">Example</span></span>  
 <span data-ttu-id="f4c86-139">Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="f4c86-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="f4c86-140">Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service.</span><span class="sxs-lookup"><span data-stu-id="f4c86-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="f4c86-141">L’exemple suivant montre le contenu d’un fichier de configuration qui contient le comportement de `MyChannelCacheBehavior` service avec le cache d’usine personnalisé et les paramètres de cache de canal.</span><span class="sxs-lookup"><span data-stu-id="f4c86-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="f4c86-142">Ce comportement de service est `behaviorConfiguration` ajouté au service grâce à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="f4c86-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4c86-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4c86-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="f4c86-144">Modification des niveaux de partage du cache pour les activités d'envoi</span><span class="sxs-lookup"><span data-stu-id="f4c86-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
