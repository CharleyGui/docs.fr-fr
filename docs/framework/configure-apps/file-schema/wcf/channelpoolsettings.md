---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398156"
---
# \<channelPoolSettings>
<span data-ttu-id="3f9cc-101">Spécifie les paramètres du pool du canal pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="3f9cc-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f9cc-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f9cc-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f9cc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3f9cc-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f9cc-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f9cc-105">Attributes</span></span>  
  
|<span data-ttu-id="3f9cc-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f9cc-106">Attribute</span></span>|<span data-ttu-id="3f9cc-107">Description</span><span class="sxs-lookup"><span data-stu-id="3f9cc-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="3f9cc-108"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité des canaux du pool avant leur déconnexion.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="3f9cc-109">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3f9cc-110"><xref:System.TimeSpan> qui spécifie l'intervalle de temps après lequel un canal, lorsqu'il est retourné au pool, est fermé.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="3f9cc-111">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="3f9cc-112">Entier positif qui spécifie le nombre maximal de canaux qui peuvent être stockés dans le pool pour chaque point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="3f9cc-113">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f9cc-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f9cc-114">Child Elements</span></span>  
 <span data-ttu-id="3f9cc-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f9cc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f9cc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3f9cc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="3f9cc-117">Element</span></span>|<span data-ttu-id="3f9cc-118">Description</span><span class="sxs-lookup"><span data-stu-id="3f9cc-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="3f9cc-119">Active le routage de paquets pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f9cc-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f9cc-120">Remarks</span></span>  
 <span data-ttu-id="3f9cc-121">Les quotas sont utilisés comme un mécanisme de stratégie pour empêcher une consommation excessive de ressources.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="3f9cc-122">Ils empêchent les attaques par déni de service (DOS) qui sont malveillantes ou involontaires.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="3f9cc-123">Utilisez cet élément lors de la définition de quotas de canal sur un canal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="3f9cc-124">`ChannelPoolSettings` spécifie trois quotas :</span><span class="sxs-lookup"><span data-stu-id="3f9cc-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="3f9cc-125">Le quota `idleTimeout` est utilisé pour atténuer des attaques par déni de service (DOS) sur le serveur qui monopolise des ressources sur une longue période.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="3f9cc-126">Sur le client, la définition de la valeur correcte peut augmenter la fiabilité de la connexion avec le service.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="3f9cc-127">La valeur par défaut est basée sur une allocation habituellement modeste de ressources.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="3f9cc-128">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3f9cc-129">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="3f9cc-130">Le quota `leaseTimeout` est utilisé pour l’intégration avec les programmes d’équilibrage de charge et pour l’amélioration de la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="3f9cc-131">La valeur par défaut est basée sur une allocation classique de ressources.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="3f9cc-132">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3f9cc-133">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="3f9cc-134">Le quota `maxOutboundChannelsPerEndpoint` définit des limites de cache sur le serveur et le client et est utilisé pour améliorer la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="3f9cc-135">La valeur par défaut est basée $$sur une allocation habituellement modeste des ressources qui sont appropriées pour un environnement de développement et de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3f9cc-136">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3f9cc-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9cc-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f9cc-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="3f9cc-138">Liaisons</span><span class="sxs-lookup"><span data-stu-id="3f9cc-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f9cc-139">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="3f9cc-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3f9cc-140">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="3f9cc-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
