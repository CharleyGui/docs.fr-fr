---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850206"
---
# <a name="baseaddresses"></a><span data-ttu-id="4f1b3-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="4f1b3-101">\<baseAddresses></span></span>
<span data-ttu-id="4f1b3-102">Représente une collection d’éléments `baseAddress`, qui sont les adresses de base d’un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="4f1b3-103">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="4f1b3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4f1b3-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4f1b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<services >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="4f1b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de service**](service.md)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="4f1b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’hôte**](host.md)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="4f1b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddresses >**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1b3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f1b3-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="4f1b3-111">Type</span><span class="sxs-lookup"><span data-stu-id="4f1b3-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f1b3-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4f1b3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f1b3-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f1b3-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="4f1b3-114">Attributes</span></span>  
 <span data-ttu-id="4f1b3-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f1b3-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4f1b3-116">Child Elements</span></span>  
  
|<span data-ttu-id="4f1b3-117">Élément</span><span class="sxs-lookup"><span data-stu-id="4f1b3-117">Element</span></span>|<span data-ttu-id="4f1b3-118">Description</span><span class="sxs-lookup"><span data-stu-id="4f1b3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f1b3-119">\<add></span><span class="sxs-lookup"><span data-stu-id="4f1b3-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="4f1b3-120">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f1b3-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4f1b3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f1b3-122">Élément</span><span class="sxs-lookup"><span data-stu-id="4f1b3-122">Element</span></span>|<span data-ttu-id="4f1b3-123">Description</span><span class="sxs-lookup"><span data-stu-id="4f1b3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f1b3-124">\<host></span><span class="sxs-lookup"><span data-stu-id="4f1b3-124">\<host></span></span>](host.md)|<span data-ttu-id="4f1b3-125">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="4f1b3-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f1b3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f1b3-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="4f1b3-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="4f1b3-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
