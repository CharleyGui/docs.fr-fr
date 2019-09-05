---
title: Élément <remove> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252336"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="9a92f-102">\<supprimer > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="9a92f-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="9a92f-103">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="9a92f-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="9a92f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a92f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a92f-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9a92f-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="9a92f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9a92f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="9a92f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9a92f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="9a92f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="9a92f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a92f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a92f-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9a92f-110">Type</span><span class="sxs-lookup"><span data-stu-id="9a92f-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a92f-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9a92f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a92f-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9a92f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a92f-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9a92f-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="9a92f-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a92f-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9a92f-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a92f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9a92f-116">Élément</span><span class="sxs-lookup"><span data-stu-id="9a92f-116">Element</span></span>|<span data-ttu-id="9a92f-117">Description</span><span class="sxs-lookup"><span data-stu-id="9a92f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a92f-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="9a92f-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="9a92f-119">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="9a92f-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a92f-120">Notes</span><span class="sxs-lookup"><span data-stu-id="9a92f-120">Remarks</span></span>  
 <span data-ttu-id="9a92f-121">L' `remove` élément supprime une `namedCache` entrée de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="9a92f-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a92f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a92f-122">See also</span></span>

- [<span data-ttu-id="9a92f-123">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="9a92f-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
