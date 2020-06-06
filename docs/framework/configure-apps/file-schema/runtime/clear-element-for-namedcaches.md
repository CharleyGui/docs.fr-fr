---
title: Élément <clear> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252763"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="4324b-102">\<clear>, élément de \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="4324b-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="4324b-103">Efface toutes les `namedCache` entrées de la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="4324b-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="4324b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4324b-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="4324b-105">Type</span><span class="sxs-lookup"><span data-stu-id="4324b-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4324b-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4324b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4324b-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4324b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4324b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="4324b-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="4324b-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4324b-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="4324b-110">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4324b-110">Parent Elements</span></span>  
  
|<span data-ttu-id="4324b-111">Élément</span><span class="sxs-lookup"><span data-stu-id="4324b-111">Element</span></span>|<span data-ttu-id="4324b-112">Description</span><span class="sxs-lookup"><span data-stu-id="4324b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="4324b-113">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="4324b-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4324b-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="4324b-114">Remarks</span></span>  
 <span data-ttu-id="4324b-115">L' `clear` élément efface toutes les `namedCache` entrées de la collection de caches nommée pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="4324b-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="4324b-116">Vous pouvez utiliser l' `clear` élément avant d’utiliser l' `add` élément pour ajouter une nouvelle entrée de cache nommée afin d’être certain qu’il n’existe aucun autre cache nommé dans la collection.</span><span class="sxs-lookup"><span data-stu-id="4324b-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4324b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4324b-117">See also</span></span>

- [<span data-ttu-id="4324b-118">\<namedCaches>, Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="4324b-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
