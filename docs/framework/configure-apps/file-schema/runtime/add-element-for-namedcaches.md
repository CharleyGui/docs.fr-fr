---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154503"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="1d58a-102">\<ajouter> Element pour \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="1d58a-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="1d58a-103">Ajoute `namedCache` une entrée `namedCaches` à la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="1d58a-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="1d58a-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d58a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d58a-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d58a-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d58a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mémoireCache>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d58a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d58a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nomméCaches>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d58a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d58a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="1d58a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d58a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d58a-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="1d58a-110">Type</span><span class="sxs-lookup"><span data-stu-id="1d58a-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d58a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1d58a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1d58a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1d58a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d58a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="1d58a-113">Attributes</span></span>  
  
|<span data-ttu-id="1d58a-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="1d58a-114">Attribute</span></span>|<span data-ttu-id="1d58a-115">Description</span><span class="sxs-lookup"><span data-stu-id="1d58a-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="1d58a-116">Une valeur d’intégrant qui spécifie la taille maximale <xref:System.Runtime.Caching.MemoryCache> autorisée (dans les mégaoctets) qu’une instance d’un peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="1d58a-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="1d58a-117">La valeur par défaut est de <xref:System.Runtime.Caching.MemoryCache> 0, ce qui signifie que les heuristiques autosizing de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d58a-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="1d58a-118">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="1d58a-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="1d58a-119">Une valeur d’intégrant entre 0 et 100 qui spécifie le pourcentage maximum de mémoire d’ordinateur physiquement installée qui peut être consommée par le cache.</span><span class="sxs-lookup"><span data-stu-id="1d58a-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="1d58a-120">La valeur par défaut est de <xref:System.Runtime.Caching.MemoryCache> 0, ce qui signifie que les heuristiques autosizing de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d58a-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="1d58a-121">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="1d58a-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="1d58a-122">Cette valeur est saisie dans le format "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="1d58a-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d58a-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1d58a-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="1d58a-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1d58a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1d58a-125">Élément</span><span class="sxs-lookup"><span data-stu-id="1d58a-125">Element</span></span>|<span data-ttu-id="1d58a-126">Description</span><span class="sxs-lookup"><span data-stu-id="1d58a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d58a-127">\<nomméCaches></span><span class="sxs-lookup"><span data-stu-id="1d58a-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="1d58a-128">Contient une collection de paramètres <xref:System.Runtime.Caching.MemoryCache> de configuration pour les instances nommées.</span><span class="sxs-lookup"><span data-stu-id="1d58a-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d58a-129">Notes </span><span class="sxs-lookup"><span data-stu-id="1d58a-129">Remarks</span></span>  
 <span data-ttu-id="1d58a-130">L’élément `add` ajoute une `namedCaches` entrée à la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="1d58a-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="1d58a-131">Vous pouvez [clear](clear-element-for-namedcaches.md) utiliser l’élément `add` clair avant d’utiliser l’élément pour être certain qu’il n’y a pas d’autres caches nommées dans la collection.</span><span class="sxs-lookup"><span data-stu-id="1d58a-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="1d58a-132">Cet élément peut être utilisé dans le fichier machine.config et dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="1d58a-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d58a-133"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1d58a-133">Example</span></span>  
 <span data-ttu-id="1d58a-134">L’exemple suivant montre comment définir `namedCache` les `namedCaches` paramètres de l’entrée par défaut de la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="1d58a-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d58a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d58a-135">See also</span></span>

- [<span data-ttu-id="1d58a-136">\<nomméCaches> Element (Cache Paramètres)</span><span class="sxs-lookup"><span data-stu-id="1d58a-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
