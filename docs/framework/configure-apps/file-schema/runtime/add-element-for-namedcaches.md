---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659031"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="16da1-102">\<Ajouter > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="16da1-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="16da1-103">Ajoute une `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="16da1-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="16da1-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="16da1-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="16da1-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="16da1-105">\<memoryCache></span></span>  
<span data-ttu-id="16da1-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="16da1-106">\<namedCaches></span></span>  
<span data-ttu-id="16da1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="16da1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16da1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16da1-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="16da1-109">Type</span><span class="sxs-lookup"><span data-stu-id="16da1-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16da1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16da1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="16da1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16da1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16da1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="16da1-112">Attributes</span></span>  
  
|<span data-ttu-id="16da1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="16da1-113">Attribute</span></span>|<span data-ttu-id="16da1-114">Description</span><span class="sxs-lookup"><span data-stu-id="16da1-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="16da1-115">Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) à laquelle une instance de <xref:System.Runtime.Caching.MemoryCache> peut croître.</span><span class="sxs-lookup"><span data-stu-id="16da1-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="16da1-116">La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="16da1-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="16da1-117">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="16da1-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="16da1-118">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache.</span><span class="sxs-lookup"><span data-stu-id="16da1-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="16da1-119">La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="16da1-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="16da1-120">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="16da1-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="16da1-121">Cette valeur est entrée au format «HH: MM: SS».</span><span class="sxs-lookup"><span data-stu-id="16da1-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16da1-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16da1-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="16da1-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16da1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="16da1-124">Élément</span><span class="sxs-lookup"><span data-stu-id="16da1-124">Element</span></span>|<span data-ttu-id="16da1-125">Description</span><span class="sxs-lookup"><span data-stu-id="16da1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16da1-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="16da1-126">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="16da1-127">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="16da1-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16da1-128">Notes</span><span class="sxs-lookup"><span data-stu-id="16da1-128">Remarks</span></span>  
 <span data-ttu-id="16da1-129">L' `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="16da1-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="16da1-130">Vous pouvez utiliser l’élément [Clear](clear-element-for-namedcaches.md) avant d’utiliser l' `add` élément pour être certain qu’il n’y a pas d’autres caches nommés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="16da1-130">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="16da1-131">Cet élément peut être utilisé dans le fichier machine. config et dans le fichier Web. config.</span><span class="sxs-lookup"><span data-stu-id="16da1-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16da1-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="16da1-132">Example</span></span>  
 <span data-ttu-id="16da1-133">L’exemple suivant montre comment définir les paramètres de l’entrée `namedCache` par défaut de `namedCaches` la collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="16da1-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16da1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16da1-134">See also</span></span>

- [<span data-ttu-id="16da1-135">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="16da1-135">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
