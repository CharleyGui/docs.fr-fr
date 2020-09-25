---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 92cd6b280305c223ee125a45724691c5205ce3c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195010"
---
# \<oneWay>

<span data-ttu-id="e6d73-101">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e6d73-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="e6d73-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d73-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6d73-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6d73-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e6d73-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e6d73-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6d73-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6d73-105">Attributes</span></span>  
  
|<span data-ttu-id="e6d73-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6d73-106">Attribute</span></span>|<span data-ttu-id="e6d73-107">Description</span><span class="sxs-lookup"><span data-stu-id="e6d73-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="e6d73-108">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="e6d73-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="e6d73-109">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="e6d73-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="e6d73-110">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="e6d73-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6d73-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6d73-111">Child Elements</span></span>  
  
|<span data-ttu-id="e6d73-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e6d73-112">Element</span></span>|<span data-ttu-id="e6d73-113">Description</span><span class="sxs-lookup"><span data-stu-id="e6d73-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="e6d73-114">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="e6d73-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6d73-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6d73-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e6d73-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e6d73-116">Element</span></span>|<span data-ttu-id="e6d73-117">Description</span><span class="sxs-lookup"><span data-stu-id="e6d73-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e6d73-118">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e6d73-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6d73-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e6d73-119">Remarks</span></span>  

 <span data-ttu-id="e6d73-120">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="e6d73-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="e6d73-121">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="e6d73-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="e6d73-122">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="e6d73-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="e6d73-123">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="e6d73-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d73-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6d73-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e6d73-125">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e6d73-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6d73-126">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="e6d73-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e6d73-127">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e6d73-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
