---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252887"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="09ff6-102">\<Ajouter > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="09ff6-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="09ff6-103">Ajoute une `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="09ff6-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="09ff6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09ff6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09ff6-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="09ff6-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="09ff6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="09ff6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="09ff6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="09ff6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="09ff6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="09ff6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ff6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09ff6-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="09ff6-110">Type</span><span class="sxs-lookup"><span data-stu-id="09ff6-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09ff6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="09ff6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09ff6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="09ff6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09ff6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="09ff6-113">Attributes</span></span>  
  
|<span data-ttu-id="09ff6-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="09ff6-114">Attribute</span></span>|<span data-ttu-id="09ff6-115">Description</span><span class="sxs-lookup"><span data-stu-id="09ff6-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="09ff6-116">Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) à laquelle une instance de <xref:System.Runtime.Caching.MemoryCache> peut croître.</span><span class="sxs-lookup"><span data-stu-id="09ff6-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="09ff6-117">La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="09ff6-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="09ff6-118">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="09ff6-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="09ff6-119">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache.</span><span class="sxs-lookup"><span data-stu-id="09ff6-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="09ff6-120">La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="09ff6-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="09ff6-121">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="09ff6-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="09ff6-122">Cette valeur est entrée au format « HH : MM : SS ».</span><span class="sxs-lookup"><span data-stu-id="09ff6-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09ff6-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09ff6-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="09ff6-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="09ff6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="09ff6-125">Élément</span><span class="sxs-lookup"><span data-stu-id="09ff6-125">Element</span></span>|<span data-ttu-id="09ff6-126">Description</span><span class="sxs-lookup"><span data-stu-id="09ff6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09ff6-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="09ff6-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="09ff6-128">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="09ff6-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09ff6-129">Notes</span><span class="sxs-lookup"><span data-stu-id="09ff6-129">Remarks</span></span>  
 <span data-ttu-id="09ff6-130">L' `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="09ff6-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="09ff6-131">Vous pouvez utiliser l’élément [Clear](clear-element-for-namedcaches.md) avant d’utiliser l' `add` élément pour être certain qu’il n’y a pas d’autres caches nommés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="09ff6-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="09ff6-132">Cet élément peut être utilisé dans le fichier machine. config et dans le fichier Web. config.</span><span class="sxs-lookup"><span data-stu-id="09ff6-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09ff6-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="09ff6-133">Example</span></span>  
 <span data-ttu-id="09ff6-134">L’exemple suivant montre comment définir les paramètres de l’entrée `namedCache` par défaut de `namedCaches` la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="09ff6-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09ff6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09ff6-135">See also</span></span>

- [<span data-ttu-id="09ff6-136">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="09ff6-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
