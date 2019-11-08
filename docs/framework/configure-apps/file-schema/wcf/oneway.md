---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738789"
---
# <a name="oneway"></a><span data-ttu-id="8ee43-101">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="8ee43-101">\<oneWay></span></span>
<span data-ttu-id="8ee43-102">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ee43-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="8ee43-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ee43-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ee43-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8ee43-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ee43-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="8ee43-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="8ee43-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8ee43-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="8ee43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="8ee43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="8ee43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**oneWay >**</span><span class="sxs-lookup"><span data-stu-id="8ee43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee43-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ee43-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ee43-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8ee43-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ee43-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8ee43-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ee43-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8ee43-112">Attributes</span></span>  
  
|<span data-ttu-id="8ee43-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="8ee43-113">Attribute</span></span>|<span data-ttu-id="8ee43-114">Description</span><span class="sxs-lookup"><span data-stu-id="8ee43-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="8ee43-115">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="8ee43-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="8ee43-116">La valeur par défaut est `false`,</span><span class="sxs-lookup"><span data-stu-id="8ee43-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="8ee43-117">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="8ee43-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ee43-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8ee43-118">Child Elements</span></span>  
  
|<span data-ttu-id="8ee43-119">Élément</span><span class="sxs-lookup"><span data-stu-id="8ee43-119">Element</span></span>|<span data-ttu-id="8ee43-120">Description</span><span class="sxs-lookup"><span data-stu-id="8ee43-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ee43-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="8ee43-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="8ee43-122">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="8ee43-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ee43-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8ee43-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8ee43-124">Élément</span><span class="sxs-lookup"><span data-stu-id="8ee43-124">Element</span></span>|<span data-ttu-id="8ee43-125">Description</span><span class="sxs-lookup"><span data-stu-id="8ee43-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ee43-126">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="8ee43-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="8ee43-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ee43-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee43-128">Notes</span><span class="sxs-lookup"><span data-stu-id="8ee43-128">Remarks</span></span>  
 <span data-ttu-id="8ee43-129">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="8ee43-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="8ee43-130">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="8ee43-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="8ee43-131">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="8ee43-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="8ee43-132">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="8ee43-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee43-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ee43-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8ee43-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8ee43-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8ee43-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="8ee43-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8ee43-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="8ee43-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8ee43-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8ee43-137">\<customBinding></span></span>](custombinding.md)
