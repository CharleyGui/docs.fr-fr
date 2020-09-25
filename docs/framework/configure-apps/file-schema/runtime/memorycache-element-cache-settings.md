---
title: <memoryCache>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 14480682c5d221216df5da3844897855d1d92a0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192423"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="b86af-102">\<memoryCache>, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="b86af-102">\<memoryCache> Element (Cache Settings)</span></span>

<span data-ttu-id="b86af-103">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="b86af-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="b86af-104">La classe <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> définit un élément [memoryCache](memorycache-element-cache-settings.md) que vous pouvez utiliser pour configurer le cache.</span><span class="sxs-lookup"><span data-stu-id="b86af-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="b86af-105">Vous pouvez utiliser plusieurs instances de la classe <xref:System.Runtime.Caching.MemoryCache> dans une même application.</span><span class="sxs-lookup"><span data-stu-id="b86af-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="b86af-106">Chaque élément `memoryCache` dans le fichier de configuration peut contenir des paramètres pour une instance <xref:System.Runtime.Caching.MemoryCache> nommée.</span><span class="sxs-lookup"><span data-stu-id="b86af-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="b86af-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b86af-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="b86af-108">Type</span><span class="sxs-lookup"><span data-stu-id="b86af-108">Type</span></span>  

 <span data-ttu-id="b86af-109">Classe<xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="b86af-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b86af-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b86af-110">Attributes and Elements</span></span>  

 <span data-ttu-id="b86af-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b86af-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b86af-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b86af-112">Attributes</span></span>  
  
|<span data-ttu-id="b86af-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b86af-113">Attribute</span></span>|<span data-ttu-id="b86af-114">Description</span><span class="sxs-lookup"><span data-stu-id="b86af-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="b86af-115">Taille de mémoire maximale, en mégaoctets, que peut atteindre une instance d’un objet <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="b86af-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="b86af-116">La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="b86af-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="b86af-117">Nom de la configuration du cache.</span><span class="sxs-lookup"><span data-stu-id="b86af-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="b86af-118">Pourcentage de mémoire physique pouvant être utilisé par le cache.</span><span class="sxs-lookup"><span data-stu-id="b86af-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="b86af-119">La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="b86af-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="b86af-120">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="b86af-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="b86af-121">La valeur est entrée au format « HH:MM:SS ».</span><span class="sxs-lookup"><span data-stu-id="b86af-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b86af-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b86af-122">Child Elements</span></span>  
  
|<span data-ttu-id="b86af-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b86af-123">Element</span></span>|<span data-ttu-id="b86af-124">Description</span><span class="sxs-lookup"><span data-stu-id="b86af-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="b86af-125">Contient une collection de paramètres de configuration pour l’instance `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="b86af-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b86af-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b86af-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b86af-127">Élément</span><span class="sxs-lookup"><span data-stu-id="b86af-127">Element</span></span>|<span data-ttu-id="b86af-128">Description</span><span class="sxs-lookup"><span data-stu-id="b86af-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="b86af-129">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b86af-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="b86af-130">Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b86af-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b86af-131">Notes</span><span class="sxs-lookup"><span data-stu-id="b86af-131">Remarks</span></span>  

 <span data-ttu-id="b86af-132">La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation concrète de la classe <xref:System.Runtime.Caching.ObjectCache> abstraite.</span><span class="sxs-lookup"><span data-stu-id="b86af-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="b86af-133">Les instances de la classe <xref:System.Runtime.Caching.MemoryCache> peuvent être fournies avec les informations de configuration tirées des fichiers de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="b86af-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="b86af-134">La section de configuration [memoryCache](memorycache-element-cache-settings.md) contient une collection de configurations `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="b86af-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="b86af-135">Quand un objet cache en mémoire est initialisé, il essaie tout d’abord de trouver une entrée `namedCaches` qui correspond au nom mentionné dans le paramètre passé au constructeur du cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="b86af-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="b86af-136">S’il trouve une entrée `namedCaches` , les informations de gestion de la mémoire et d’interrogation sont récupérées à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b86af-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="b86af-137">Le processus d’initialisation détermine ensuite si des entrées de configuration ont été substituées, en utilisant la collection facultative de paires nom/valeur d’informations de configuration dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="b86af-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="b86af-138">Si vous passez l’une des valeurs suivantes dans la collection de paires nom/valeur, ces valeurs remplacent les informations obtenues à partir du fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="b86af-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="b86af-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="b86af-139">Example</span></span>  

 <span data-ttu-id="b86af-140">L’exemple suivant montre comment définir le nom de l' <xref:System.Runtime.Caching.MemoryCache> objet dans le cache par défaut en affectant à l' `name` attribut la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="b86af-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="b86af-141">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryLimitPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="b86af-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="b86af-142">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="b86af-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="b86af-143">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="b86af-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b86af-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b86af-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="b86af-145">\<system.runtime.caching> , Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="b86af-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="b86af-146">\<namedCaches> , Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="b86af-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
