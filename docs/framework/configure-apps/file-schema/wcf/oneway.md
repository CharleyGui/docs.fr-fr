---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932945"
---
# <a name="oneway"></a><span data-ttu-id="1a5b5-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="1a5b5-101">\<oneWay></span></span>
<span data-ttu-id="1a5b5-102">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="1a5b5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1a5b5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1a5b5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1a5b5-104">\<bindings></span></span>  
<span data-ttu-id="1a5b5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1a5b5-105">\<customBinding></span></span>  
<span data-ttu-id="1a5b5-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="1a5b5-106">\<binding></span></span>  
<span data-ttu-id="1a5b5-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="1a5b5-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5b5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a5b5-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a5b5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1a5b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a5b5-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a5b5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1a5b5-111">Attributes</span></span>  
  
|<span data-ttu-id="1a5b5-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="1a5b5-112">Attribute</span></span>|<span data-ttu-id="1a5b5-113">Description</span><span class="sxs-lookup"><span data-stu-id="1a5b5-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="1a5b5-114">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="1a5b5-115">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="1a5b5-116">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a5b5-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1a5b5-117">Child Elements</span></span>  
  
|<span data-ttu-id="1a5b5-118">Élément</span><span class="sxs-lookup"><span data-stu-id="1a5b5-118">Element</span></span>|<span data-ttu-id="1a5b5-119">Description</span><span class="sxs-lookup"><span data-stu-id="1a5b5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a5b5-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="1a5b5-120">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="1a5b5-121">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a5b5-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1a5b5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1a5b5-123">Élément</span><span class="sxs-lookup"><span data-stu-id="1a5b5-123">Element</span></span>|<span data-ttu-id="1a5b5-124">Description</span><span class="sxs-lookup"><span data-stu-id="1a5b5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a5b5-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="1a5b5-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1a5b5-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a5b5-127">Notes</span><span class="sxs-lookup"><span data-stu-id="1a5b5-127">Remarks</span></span>  
 <span data-ttu-id="1a5b5-128">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="1a5b5-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="1a5b5-129">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="1a5b5-130">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="1a5b5-131">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="1a5b5-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5b5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a5b5-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1a5b5-133">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1a5b5-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1a5b5-134">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="1a5b5-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1a5b5-135">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="1a5b5-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1a5b5-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1a5b5-136">\<customBinding></span></span>](custombinding.md)
