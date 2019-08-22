---
title: Élément <clear> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658860"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="e5a5c-102">\<Effacer > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="e5a5c-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="e5a5c-103">Efface toutes `namedCache` les entrées de `namedCaches` la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="e5a5c-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="e5a5c-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="e5a5c-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="e5a5c-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="e5a5c-105">\<memoryCache></span></span>  
<span data-ttu-id="e5a5c-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="e5a5c-106">\<namedCaches></span></span>  
<span data-ttu-id="e5a5c-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e5a5c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a5c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5a5c-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="e5a5c-109">Type</span><span class="sxs-lookup"><span data-stu-id="e5a5c-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5a5c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5a5c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e5a5c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e5a5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5a5c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5a5c-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="e5a5c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5a5c-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="e5a5c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5a5c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e5a5c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e5a5c-115">Element</span></span>|<span data-ttu-id="e5a5c-116">Description</span><span class="sxs-lookup"><span data-stu-id="e5a5c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5a5c-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="e5a5c-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="e5a5c-118">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="e5a5c-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5a5c-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e5a5c-119">Remarks</span></span>  
 <span data-ttu-id="e5a5c-120">L' `clear` élément efface toutes `namedCache` les entrées de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="e5a5c-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="e5a5c-121">Vous pouvez utiliser l' `clear` élément avant d’utiliser l' `add` élément pour ajouter une nouvelle entrée de cache nommée afin d’être certain qu’il n’existe aucun autre cache nommé dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e5a5c-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a5c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5a5c-122">See also</span></span>

- [<span data-ttu-id="e5a5c-123">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="e5a5c-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
