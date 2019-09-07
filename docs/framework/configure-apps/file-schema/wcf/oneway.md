---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f12969d8b752e54916b45c3d0e64f114971b8944
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397649"
---
# <a name="oneway"></a><span data-ttu-id="95b57-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="95b57-101">\<oneWay></span></span>
<span data-ttu-id="95b57-102">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="95b57-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="95b57-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95b57-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95b57-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="95b57-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="95b57-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="95b57-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="95b57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="95b57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="95b57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="95b57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="95b57-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oneWay**</span><span class="sxs-lookup"><span data-stu-id="95b57-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b57-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95b57-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95b57-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95b57-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95b57-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95b57-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95b57-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="95b57-112">Attributes</span></span>  
  
|<span data-ttu-id="95b57-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="95b57-113">Attribute</span></span>|<span data-ttu-id="95b57-114">Description</span><span class="sxs-lookup"><span data-stu-id="95b57-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="95b57-115">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="95b57-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="95b57-116">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="95b57-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="95b57-117">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="95b57-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95b57-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95b57-118">Child Elements</span></span>  
  
|<span data-ttu-id="95b57-119">Élément</span><span class="sxs-lookup"><span data-stu-id="95b57-119">Element</span></span>|<span data-ttu-id="95b57-120">Description</span><span class="sxs-lookup"><span data-stu-id="95b57-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95b57-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="95b57-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="95b57-122">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="95b57-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95b57-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95b57-123">Parent Elements</span></span>  
  
|<span data-ttu-id="95b57-124">Élément</span><span class="sxs-lookup"><span data-stu-id="95b57-124">Element</span></span>|<span data-ttu-id="95b57-125">Description</span><span class="sxs-lookup"><span data-stu-id="95b57-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95b57-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="95b57-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="95b57-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="95b57-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95b57-128">Notes</span><span class="sxs-lookup"><span data-stu-id="95b57-128">Remarks</span></span>  
 <span data-ttu-id="95b57-129">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="95b57-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="95b57-130">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="95b57-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="95b57-131">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="95b57-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="95b57-132">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="95b57-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b57-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95b57-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="95b57-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="95b57-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="95b57-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="95b57-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="95b57-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="95b57-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="95b57-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="95b57-137">\<customBinding></span></span>](custombinding.md)
