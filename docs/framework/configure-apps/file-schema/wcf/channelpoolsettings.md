---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 70f7452a22ae08d6eccd7d3644bdc8df45087ae0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423188"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="9eaf5-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="9eaf5-101">\<channelPoolSettings></span></span>
<span data-ttu-id="9eaf5-102">Spécifie les paramètres du pool du canal pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="9eaf5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9eaf5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="9eaf5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9eaf5-104">\<bindings></span></span>  
<span data-ttu-id="9eaf5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9eaf5-105">\<customBinding></span></span>  
<span data-ttu-id="9eaf5-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="9eaf5-106">\<binding></span></span>  
<span data-ttu-id="9eaf5-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9eaf5-107">\<oneWay></span></span>  
<span data-ttu-id="9eaf5-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="9eaf5-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eaf5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eaf5-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eaf5-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9eaf5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9eaf5-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eaf5-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9eaf5-112">Attributes</span></span>  
  
|<span data-ttu-id="9eaf5-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9eaf5-113">Attribute</span></span>|<span data-ttu-id="9eaf5-114">Description</span><span class="sxs-lookup"><span data-stu-id="9eaf5-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="9eaf5-115"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité des canaux du pool avant leur déconnexion.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="9eaf5-116">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="9eaf5-117"><xref:System.TimeSpan> qui spécifie l'intervalle de temps après lequel un canal, lorsqu'il est retourné au pool, est fermé.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="9eaf5-118">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="9eaf5-119">Entier positif qui spécifie le nombre maximal de canaux qui peuvent être stockés dans le pool pour chaque point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="9eaf5-120">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9eaf5-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9eaf5-121">Child Elements</span></span>  
 <span data-ttu-id="9eaf5-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eaf5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9eaf5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9eaf5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="9eaf5-124">Element</span></span>|<span data-ttu-id="9eaf5-125">Description</span><span class="sxs-lookup"><span data-stu-id="9eaf5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9eaf5-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9eaf5-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="9eaf5-127">Active le routage de paquets pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eaf5-128">Notes</span><span class="sxs-lookup"><span data-stu-id="9eaf5-128">Remarks</span></span>  
 <span data-ttu-id="9eaf5-129">Les quotas sont utilisés comme un mécanisme de stratégie pour empêcher une consommation excessive de ressources.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="9eaf5-130">Ils empêchent les attaques par déni de service (DOS) qui sont malveillantes ou involontaires.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="9eaf5-131">Utilisez cet élément lors de la définition de quotas de canal sur un canal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="9eaf5-132">`ChannelPoolSettings` spécifie trois quotas :</span><span class="sxs-lookup"><span data-stu-id="9eaf5-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="9eaf5-133">Le quota `idleTimeout` est utilisé pour atténuer des attaques par déni de service (DOS) sur le serveur qui monopolise des ressources sur une longue période.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="9eaf5-134">Sur le client, la définition de la valeur correcte peut augmenter la fiabilité de la connexion avec le service.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="9eaf5-135">La valeur par défaut est basée sur une allocation habituellement modeste de ressources.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="9eaf5-136">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9eaf5-137">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="9eaf5-138">Le quota `leaseTimeout` est utilisé pour l’intégration avec les programmes d’équilibrage de charge et pour l’amélioration de la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="9eaf5-139">La valeur par défaut est basée sur une allocation classique de ressources.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="9eaf5-140">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9eaf5-141">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="9eaf5-142">Le quota `maxOutboundChannelsPerEndpoint` définit des limites de cache sur le serveur et le client et est utilisé pour améliorer la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="9eaf5-143">La valeur par défaut est basée $$sur une allocation habituellement modeste des ressources qui sont appropriées pour un environnement de développement et de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9eaf5-144">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eaf5-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eaf5-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9eaf5-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9eaf5-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="9eaf5-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9eaf5-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9eaf5-148">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="9eaf5-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9eaf5-149">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="9eaf5-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9eaf5-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9eaf5-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
