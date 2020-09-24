---
title: Élément <remove> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: c8ad5a0ce6d7a3059943b3962b9255385cea6e15
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183986"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="76816-102">\<remove>, élément de \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="76816-102">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="76816-103">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="76816-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="76816-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76816-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="76816-105">Type</span><span class="sxs-lookup"><span data-stu-id="76816-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76816-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="76816-106">Attributes and Elements</span></span>  

 <span data-ttu-id="76816-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="76816-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76816-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="76816-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="76816-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="76816-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="76816-110">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="76816-110">Parent Elements</span></span>  
  
|<span data-ttu-id="76816-111">Élément</span><span class="sxs-lookup"><span data-stu-id="76816-111">Element</span></span>|<span data-ttu-id="76816-112">Description</span><span class="sxs-lookup"><span data-stu-id="76816-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="76816-113">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="76816-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76816-114">Notes</span><span class="sxs-lookup"><span data-stu-id="76816-114">Remarks</span></span>  

 <span data-ttu-id="76816-115">L' `remove` élément supprime une `namedCache` entrée de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="76816-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76816-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76816-116">See also</span></span>

- [<span data-ttu-id="76816-117">\<namedCaches> , Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="76816-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
