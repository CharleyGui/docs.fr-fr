---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 2ad1cba170a7ade06de4678651a8dfcb608d5c46
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607211"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="2c341-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="2c341-101">\<channelPoolSettings></span></span>
<span data-ttu-id="2c341-102">Spécifie les paramètres du pool du canal pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2c341-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="2c341-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c341-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2c341-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2c341-104">\<bindings></span></span>  
<span data-ttu-id="2c341-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2c341-105">\<customBinding></span></span>  
<span data-ttu-id="2c341-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="2c341-106">\<binding></span></span>  
<span data-ttu-id="2c341-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2c341-107">\<oneWay></span></span>  
<span data-ttu-id="2c341-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="2c341-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c341-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c341-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c341-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2c341-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c341-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2c341-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c341-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="2c341-112">Attributes</span></span>  
  
|<span data-ttu-id="2c341-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="2c341-113">Attribute</span></span>|<span data-ttu-id="2c341-114">Description</span><span class="sxs-lookup"><span data-stu-id="2c341-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="2c341-115"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité des canaux du pool avant leur déconnexion.</span><span class="sxs-lookup"><span data-stu-id="2c341-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="2c341-116">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="2c341-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="2c341-117"><xref:System.TimeSpan> qui spécifie l'intervalle de temps après lequel un canal, lorsqu'il est retourné au pool, est fermé.</span><span class="sxs-lookup"><span data-stu-id="2c341-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="2c341-118">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2c341-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="2c341-119">Entier positif qui spécifie le nombre maximal de canaux qui peuvent être stockés dans le pool pour chaque point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="2c341-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="2c341-120">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="2c341-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c341-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2c341-121">Child Elements</span></span>  
 <span data-ttu-id="2c341-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2c341-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c341-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2c341-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2c341-124">Élément</span><span class="sxs-lookup"><span data-stu-id="2c341-124">Element</span></span>|<span data-ttu-id="2c341-125">Description</span><span class="sxs-lookup"><span data-stu-id="2c341-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c341-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2c341-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="2c341-127">Active le routage de paquets pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2c341-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c341-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2c341-128">Remarks</span></span>  
 <span data-ttu-id="2c341-129">Les quotas sont utilisés comme un mécanisme de stratégie pour empêcher une consommation excessive de ressources.</span><span class="sxs-lookup"><span data-stu-id="2c341-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="2c341-130">Ils empêchent les attaques par déni de service (DOS) qui sont malveillantes ou involontaires.</span><span class="sxs-lookup"><span data-stu-id="2c341-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="2c341-131">Utilisez cet élément lors de la définition de quotas de canal sur un canal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c341-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="2c341-132">`ChannelPoolSettings` spécifie trois quotas :</span><span class="sxs-lookup"><span data-stu-id="2c341-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="2c341-133">Le quota `idleTimeout` est utilisé pour atténuer des attaques par déni de service (DOS) sur le serveur qui monopolise des ressources sur une longue période.</span><span class="sxs-lookup"><span data-stu-id="2c341-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="2c341-134">Sur le client, la définition de la valeur correcte peut augmenter la fiabilité de la connexion avec le service.</span><span class="sxs-lookup"><span data-stu-id="2c341-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="2c341-135">La valeur par défaut est basée sur une allocation habituellement modeste de ressources.</span><span class="sxs-lookup"><span data-stu-id="2c341-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="2c341-136">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="2c341-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2c341-137">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2c341-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="2c341-138">Le quota `leaseTimeout` est utilisé pour l’intégration avec les programmes d’équilibrage de charge et pour l’amélioration de la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="2c341-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="2c341-139">La valeur par défaut est basée sur une allocation classique de ressources.</span><span class="sxs-lookup"><span data-stu-id="2c341-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="2c341-140">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="2c341-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2c341-141">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2c341-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="2c341-142">Le quota `maxOutboundChannelsPerEndpoint` définit des limites de cache sur le serveur et le client et est utilisé pour améliorer la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="2c341-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="2c341-143">La valeur par défaut est basée $$sur une allocation habituellement modeste des ressources qui sont appropriées pour un environnement de développement et de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="2c341-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2c341-144">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2c341-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c341-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c341-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2c341-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2c341-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="2c341-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2c341-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2c341-148">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="2c341-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2c341-149">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2c341-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2c341-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2c341-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
