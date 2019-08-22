---
title: Élément <remove> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: e9b126cee83bc8109606d915ea48549beea970c9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663474"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="55f78-102">\<supprimer > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="55f78-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="55f78-103">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="55f78-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="55f78-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="55f78-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="55f78-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="55f78-105">\<memoryCache></span></span>  
<span data-ttu-id="55f78-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="55f78-106">\<namedCaches></span></span>  
<span data-ttu-id="55f78-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="55f78-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f78-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55f78-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="55f78-109">Type</span><span class="sxs-lookup"><span data-stu-id="55f78-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55f78-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55f78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55f78-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55f78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55f78-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="55f78-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="55f78-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55f78-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="55f78-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55f78-114">Parent Elements</span></span>  
  
|<span data-ttu-id="55f78-115">Élément</span><span class="sxs-lookup"><span data-stu-id="55f78-115">Element</span></span>|<span data-ttu-id="55f78-116">Description</span><span class="sxs-lookup"><span data-stu-id="55f78-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55f78-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="55f78-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="55f78-118">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="55f78-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f78-119">Notes</span><span class="sxs-lookup"><span data-stu-id="55f78-119">Remarks</span></span>  
 <span data-ttu-id="55f78-120">L' `remove` élément supprime une `namedCache` entrée de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="55f78-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f78-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55f78-121">See also</span></span>

- [<span data-ttu-id="55f78-122">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="55f78-122">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
