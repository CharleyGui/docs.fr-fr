---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: c1775ddabffda58c7529a64b89c9c53ff3da7b99
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164920"
---
# \<sendMessageChannelCache>

<span data-ttu-id="c1aa4-101">Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-101">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a><span data-ttu-id="c1aa4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1aa4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1aa4-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c1aa4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c1aa4-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1aa4-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="c1aa4-105">Attributes</span></span>  
  
|<span data-ttu-id="c1aa4-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="c1aa4-106">Attribute</span></span>|<span data-ttu-id="c1aa4-107">Description</span><span class="sxs-lookup"><span data-stu-id="c1aa4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1aa4-108">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="c1aa4-108">allowUnsafeCaching</span></span>|<span data-ttu-id="c1aa4-109">Valeur booléenne qui indique s'il faut activer la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-109">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="c1aa4-110">Si le service de flux de travail comporte des liaisons ou des comportements personnalisés, la mise en cache pourrait être non sécurisée et donc désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-110">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="c1aa4-111">Toutefois, si vous souhaitez activer la mise en cache, affectez la valeur **true**à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-111">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1aa4-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c1aa4-112">Child Elements</span></span>  
  
|<span data-ttu-id="c1aa4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c1aa4-113">Element</span></span>|<span data-ttu-id="c1aa4-114">Description</span><span class="sxs-lookup"><span data-stu-id="c1aa4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|<span data-ttu-id="c1aa4-115">Spécifie les paramètres du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-115">Specifies the settings of the channel cache.</span></span>|  
|[\<factorySettings>](factorysettings.md)|<span data-ttu-id="c1aa4-116">Spécifie les paramètres du cache de la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-116">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1aa4-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c1aa4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c1aa4-118">Élément</span><span class="sxs-lookup"><span data-stu-id="c1aa4-118">Element</span></span>|<span data-ttu-id="c1aa4-119">Description</span><span class="sxs-lookup"><span data-stu-id="c1aa4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1aa4-120">\<behavior> of \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1aa4-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c1aa4-121">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-121">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1aa4-122">Notes</span><span class="sxs-lookup"><span data-stu-id="c1aa4-122">Remarks</span></span>  

 <span data-ttu-id="c1aa4-123">Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-123">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="c1aa4-124">Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-124">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="c1aa4-125">Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="c1aa4-125">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="c1aa4-126">Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance).</span><span class="sxs-lookup"><span data-stu-id="c1aa4-126">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="c1aa4-127">La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-127">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="c1aa4-128">Pour plus d’informations sur la modification des niveaux de partage de cache par défaut et des paramètres de cache pour la fabrique de canaux et le cache de canaux, consultez [modification des niveaux de partage du cache pour les activités d’envoi](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="c1aa4-128">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1aa4-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1aa4-129">Example</span></span>  

 <span data-ttu-id="c1aa4-130">Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-130">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="c1aa4-131">Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-131">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="c1aa4-132">L’exemple suivant montre le contenu d’un fichier de configuration qui contient le `MyChannelCacheBehavior`  comportement de service avec les paramètres du cache de fabrique personnalisé et du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-132">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="c1aa4-133">Ce comportement de service est ajouté au service via l' `behaviorConfiguration` attribut.</span><span class="sxs-lookup"><span data-stu-id="c1aa4-133">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1aa4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1aa4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="c1aa4-135">Modification des niveaux de partage du cache pour les activités d'envoi</span><span class="sxs-lookup"><span data-stu-id="c1aa4-135">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
