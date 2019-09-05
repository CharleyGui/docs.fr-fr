---
title: <memoryCache>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25467fc751ad772e74ca714e6059bc5134300ed6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252486"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="43ab0-102">\<memoryCache >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="43ab0-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="43ab0-103">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="43ab0-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="43ab0-104">La classe <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> définit un élément [memoryCache](memorycache-element-cache-settings.md) que vous pouvez utiliser pour configurer le cache.</span><span class="sxs-lookup"><span data-stu-id="43ab0-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="43ab0-105">Vous pouvez utiliser plusieurs instances de la classe <xref:System.Runtime.Caching.MemoryCache> dans une même application.</span><span class="sxs-lookup"><span data-stu-id="43ab0-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="43ab0-106">Chaque élément `memoryCache` dans le fichier de configuration peut contenir des paramètres pour une instance <xref:System.Runtime.Caching.MemoryCache> nommée.</span><span class="sxs-lookup"><span data-stu-id="43ab0-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="43ab0-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43ab0-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43ab0-108">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="43ab0-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="43ab0-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<> memoryCache**</span><span class="sxs-lookup"><span data-stu-id="43ab0-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ab0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43ab0-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="43ab0-111">Type</span><span class="sxs-lookup"><span data-stu-id="43ab0-111">Type</span></span>  
 <span data-ttu-id="43ab0-112">Classe<xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="43ab0-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ab0-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="43ab0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="43ab0-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="43ab0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ab0-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="43ab0-115">Attributes</span></span>  
  
|<span data-ttu-id="43ab0-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="43ab0-116">Attribute</span></span>|<span data-ttu-id="43ab0-117">Description</span><span class="sxs-lookup"><span data-stu-id="43ab0-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="43ab0-118">Taille de mémoire maximale, en mégaoctets, que peut atteindre une instance d’un objet <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="43ab0-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="43ab0-119">La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="43ab0-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="43ab0-120">Nom de la configuration du cache.</span><span class="sxs-lookup"><span data-stu-id="43ab0-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="43ab0-121">Pourcentage de mémoire physique pouvant être utilisé par le cache.</span><span class="sxs-lookup"><span data-stu-id="43ab0-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="43ab0-122">La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="43ab0-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="43ab0-123">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="43ab0-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="43ab0-124">La valeur est entrée au format « HH:MM:SS ».</span><span class="sxs-lookup"><span data-stu-id="43ab0-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43ab0-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="43ab0-125">Child Elements</span></span>  
  
|<span data-ttu-id="43ab0-126">Élément</span><span class="sxs-lookup"><span data-stu-id="43ab0-126">Element</span></span>|<span data-ttu-id="43ab0-127">Description</span><span class="sxs-lookup"><span data-stu-id="43ab0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43ab0-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="43ab0-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="43ab0-129">Contient une collection de paramètres de configuration pour l’instance `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="43ab0-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43ab0-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="43ab0-130">Parent Elements</span></span>  
  
|<span data-ttu-id="43ab0-131">Élément</span><span class="sxs-lookup"><span data-stu-id="43ab0-131">Element</span></span>|<span data-ttu-id="43ab0-132">Description</span><span class="sxs-lookup"><span data-stu-id="43ab0-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43ab0-133">\<configuration></span><span class="sxs-lookup"><span data-stu-id="43ab0-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="43ab0-134">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43ab0-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="43ab0-135">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="43ab0-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="43ab0-136">Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43ab0-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ab0-137">Notes</span><span class="sxs-lookup"><span data-stu-id="43ab0-137">Remarks</span></span>  
 <span data-ttu-id="43ab0-138">La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation concrète de la classe <xref:System.Runtime.Caching.ObjectCache> abstraite.</span><span class="sxs-lookup"><span data-stu-id="43ab0-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="43ab0-139">Les instances de la classe <xref:System.Runtime.Caching.MemoryCache> peuvent être fournies avec les informations de configuration tirées des fichiers de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="43ab0-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="43ab0-140">La section de configuration [memoryCache](memorycache-element-cache-settings.md) contient une collection de configurations `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="43ab0-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="43ab0-141">Quand un objet cache en mémoire est initialisé, il essaie tout d’abord de trouver une entrée `namedCaches` qui correspond au nom mentionné dans le paramètre passé au constructeur du cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="43ab0-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="43ab0-142">S’il trouve une entrée `namedCaches` , les informations de gestion de la mémoire et d’interrogation sont récupérées à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="43ab0-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="43ab0-143">Le processus d’initialisation détermine ensuite si des entrées de configuration ont été substituées, en utilisant la collection facultative de paires nom/valeur d’informations de configuration dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="43ab0-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="43ab0-144">Si vous passez l’une des valeurs suivantes dans la collection de paires nom/valeur, ces valeurs remplacent les informations obtenues à partir du fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="43ab0-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="43ab0-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="43ab0-145">Example</span></span>  
 <span data-ttu-id="43ab0-146">L’exemple suivant montre comment définir le nom de l' <xref:System.Runtime.Caching.MemoryCache> objet dans le cache par défaut en affectant à l' `name` attribut la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="43ab0-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="43ab0-147">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryLimitPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="43ab0-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="43ab0-148">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="43ab0-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="43ab0-149">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="43ab0-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43ab0-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43ab0-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="43ab0-151">\<System. Runtime. Caching >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="43ab0-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="43ab0-152">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="43ab0-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
