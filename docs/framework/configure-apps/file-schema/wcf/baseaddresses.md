---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926425"
---
# <a name="baseaddresses"></a><span data-ttu-id="d26b3-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="d26b3-101">\<baseAddresses></span></span>
<span data-ttu-id="d26b3-102">Représente une collection d’éléments `baseAddress`, qui sont les adresses de base d’un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="d26b3-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="d26b3-103">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="d26b3-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="d26b3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d26b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d26b3-105">\<client></span><span class="sxs-lookup"><span data-stu-id="d26b3-105">\<client></span></span>  
<span data-ttu-id="d26b3-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d26b3-106">\<endpoint></span></span>  
<span data-ttu-id="d26b3-107">\<host></span><span class="sxs-lookup"><span data-stu-id="d26b3-107">\<host></span></span>  
<span data-ttu-id="d26b3-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="d26b3-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26b3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d26b3-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="d26b3-110">Type</span><span class="sxs-lookup"><span data-stu-id="d26b3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d26b3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d26b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d26b3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d26b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d26b3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d26b3-113">Attributes</span></span>  
 <span data-ttu-id="d26b3-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d26b3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d26b3-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d26b3-115">Child Elements</span></span>  
  
|<span data-ttu-id="d26b3-116">Élément</span><span class="sxs-lookup"><span data-stu-id="d26b3-116">Element</span></span>|<span data-ttu-id="d26b3-117">Description</span><span class="sxs-lookup"><span data-stu-id="d26b3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d26b3-118">\<add></span><span class="sxs-lookup"><span data-stu-id="d26b3-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="d26b3-119">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="d26b3-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d26b3-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d26b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d26b3-121">Élément</span><span class="sxs-lookup"><span data-stu-id="d26b3-121">Element</span></span>|<span data-ttu-id="d26b3-122">Description</span><span class="sxs-lookup"><span data-stu-id="d26b3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d26b3-123">\<host></span><span class="sxs-lookup"><span data-stu-id="d26b3-123">\<host></span></span>](host.md)|<span data-ttu-id="d26b3-124">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="d26b3-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d26b3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d26b3-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="d26b3-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="d26b3-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
