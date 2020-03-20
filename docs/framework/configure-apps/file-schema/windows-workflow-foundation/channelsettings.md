---
title: <channelSettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
ms.openlocfilehash: f6a57e2cc1e7c5e114fd38ee3534ab7c4e629b36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152272"
---
# <a name="channelsettings"></a><span data-ttu-id="2f851-101">\<canauxSettings></span><span class="sxs-lookup"><span data-stu-id="2f851-101">\<channelSettings></span></span>
<span data-ttu-id="2f851-102">Spécifie les paramètres du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="2f851-102">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="2f851-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f851-104">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2f851-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportements>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2f851-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2f851-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportement>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2f851-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<envoyerMessageChannelCache>**](sendmessagechannelcache.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span></span>\
<span data-ttu-id="2f851-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<canauxSettings>**</span><span class="sxs-lookup"><span data-stu-id="2f851-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f851-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f851-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f851-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f851-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2f851-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f851-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f851-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f851-113">Attributes</span></span>  
  
|<span data-ttu-id="2f851-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f851-114">Attribute</span></span>|<span data-ttu-id="2f851-115">Description</span><span class="sxs-lookup"><span data-stu-id="2f851-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f851-116">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="2f851-116">idleTimeout</span></span>|<span data-ttu-id="2f851-117">Valeur TimeSpan qui spécifie la durée maximale pendant laquelle l'objet peut rester inactif dans le cache avant d'être supprimé.</span><span class="sxs-lookup"><span data-stu-id="2f851-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="2f851-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="2f851-118">leaseTimeout</span></span>|<span data-ttu-id="2f851-119">Valeur TimeSpan qui spécifie le délai au bout duquel un objet est supprimé du cache.</span><span class="sxs-lookup"><span data-stu-id="2f851-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="2f851-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="2f851-120">maxItemsInCache</span></span>|<span data-ttu-id="2f851-121">Entier qui spécifie le nombre maximal d'objets pouvant être placés dans le cache.</span><span class="sxs-lookup"><span data-stu-id="2f851-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f851-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f851-122">Child Elements</span></span>  
 <span data-ttu-id="2f851-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2f851-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f851-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f851-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2f851-125">Élément</span><span class="sxs-lookup"><span data-stu-id="2f851-125">Element</span></span>|<span data-ttu-id="2f851-126">Description</span><span class="sxs-lookup"><span data-stu-id="2f851-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f851-127">\<envoyerMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="2f851-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="2f851-128">Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="2f851-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f851-129">Notes </span><span class="sxs-lookup"><span data-stu-id="2f851-129">Remarks</span></span>  
 <span data-ttu-id="2f851-130">Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="2f851-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="2f851-131">Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2f851-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="2f851-132">Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="2f851-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="2f851-133">Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance).</span><span class="sxs-lookup"><span data-stu-id="2f851-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="2f851-134">La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="2f851-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="2f851-135">Pour plus d’informations sur la façon de modifier les niveaux de partage de cache par défaut et les paramètres de cache pour l’usine de canaux et le cache de canal, voir [Changer les niveaux de partage de cache pour envoyer des activités](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="2f851-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f851-136"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2f851-136">Example</span></span>  
 <span data-ttu-id="2f851-137">Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="2f851-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="2f851-138">Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service.</span><span class="sxs-lookup"><span data-stu-id="2f851-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="2f851-139">L’exemple suivant montre le contenu d’un fichier de configuration qui contient le comportement de `MyChannelCacheBehavior` service avec le cache d’usine personnalisé et les paramètres de cache de canal.</span><span class="sxs-lookup"><span data-stu-id="2f851-139">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="2f851-140">Ce comportement de service est `behaviorConfiguration` ajouté au service grâce à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="2f851-140">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f851-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f851-141">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="2f851-142">Modification des niveaux de partage du cache pour les activités d'envoi</span><span class="sxs-lookup"><span data-stu-id="2f851-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
