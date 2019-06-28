---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: b0487ba5025557f07d9991f911cd71a677a04e2c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423375"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="ac451-102">\<Ajouter > élément pour \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="ac451-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="ac451-103">Ajoute un `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="ac451-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="ac451-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="ac451-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="ac451-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="ac451-105">\<memoryCache></span></span>  
<span data-ttu-id="ac451-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="ac451-106">\<namedCaches></span></span>  
<span data-ttu-id="ac451-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ac451-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac451-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac451-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ac451-109">Type</span><span class="sxs-lookup"><span data-stu-id="ac451-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac451-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac451-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac451-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ac451-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac451-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac451-112">Attributes</span></span>  
  
|<span data-ttu-id="ac451-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac451-113">Attribute</span></span>|<span data-ttu-id="ac451-114">Description</span><span class="sxs-lookup"><span data-stu-id="ac451-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="ac451-115">Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) qui une instance d’un <xref:System.Runtime.Caching.MemoryCache> peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="ac451-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="ac451-116">La valeur par défaut est 0, ce qui signifie que le <xref:System.Runtime.Caching.MemoryCache> heuristiques à dimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="ac451-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="ac451-117">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="ac451-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="ac451-118">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire d’ordinateur physiquement installé qui peut être utilisé par le cache.</span><span class="sxs-lookup"><span data-stu-id="ac451-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="ac451-119">La valeur par défaut est 0, ce qui signifie que le <xref:System.Runtime.Caching.MemoryCache> heuristiques à dimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="ac451-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="ac451-120">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="ac451-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="ac451-121">Cette valeur est entrée au format « Hh ».</span><span class="sxs-lookup"><span data-stu-id="ac451-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac451-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac451-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ac451-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac451-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ac451-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ac451-124">Element</span></span>|<span data-ttu-id="ac451-125">Description</span><span class="sxs-lookup"><span data-stu-id="ac451-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac451-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="ac451-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="ac451-127">Contient une collection de paramètres de configuration pour l’élément nommé <xref:System.Runtime.Caching.MemoryCache> instances.</span><span class="sxs-lookup"><span data-stu-id="ac451-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac451-128">Notes</span><span class="sxs-lookup"><span data-stu-id="ac451-128">Remarks</span></span>  
 <span data-ttu-id="ac451-129">Le `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="ac451-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="ac451-130">Vous pouvez utiliser la [effacer](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) élément avant d’utiliser le `add` élément qu’il n’existe aucun autre cache nommé dans la collection.</span><span class="sxs-lookup"><span data-stu-id="ac451-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="ac451-131">Cet élément peut être utilisé dans le fichier machine.config et dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="ac451-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac451-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac451-132">Example</span></span>  
 <span data-ttu-id="ac451-133">L’exemple suivant montre comment définir les paramètres de la valeur par défaut `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="ac451-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac451-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac451-134">See also</span></span>

- [<span data-ttu-id="ac451-135">\<namedCaches >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="ac451-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
