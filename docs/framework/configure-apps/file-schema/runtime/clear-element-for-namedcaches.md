---
title: Élément <clear> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252763"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="28f2b-102">\<Effacer > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="28f2b-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="28f2b-103">Efface toutes `namedCache` les entrées de `namedCaches` la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="28f2b-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="28f2b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28f2b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28f2b-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="28f2b-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="28f2b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="28f2b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="28f2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="28f2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="28f2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<désactivez >**</span><span class="sxs-lookup"><span data-stu-id="28f2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f2b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28f2b-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="28f2b-110">Type</span><span class="sxs-lookup"><span data-stu-id="28f2b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28f2b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="28f2b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28f2b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="28f2b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28f2b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="28f2b-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="28f2b-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="28f2b-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="28f2b-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="28f2b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="28f2b-116">Élément</span><span class="sxs-lookup"><span data-stu-id="28f2b-116">Element</span></span>|<span data-ttu-id="28f2b-117">Description</span><span class="sxs-lookup"><span data-stu-id="28f2b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28f2b-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="28f2b-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="28f2b-119">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="28f2b-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28f2b-120">Notes</span><span class="sxs-lookup"><span data-stu-id="28f2b-120">Remarks</span></span>  
 <span data-ttu-id="28f2b-121">L' `clear` élément efface toutes `namedCache` les entrées de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="28f2b-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="28f2b-122">Vous pouvez utiliser l' `clear` élément avant d’utiliser l' `add` élément pour ajouter une nouvelle entrée de cache nommée afin d’être certain qu’il n’existe aucun autre cache nommé dans la collection.</span><span class="sxs-lookup"><span data-stu-id="28f2b-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f2b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28f2b-123">See also</span></span>

- [<span data-ttu-id="28f2b-124">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="28f2b-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
