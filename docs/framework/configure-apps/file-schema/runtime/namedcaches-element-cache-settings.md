---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252460"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="3eee3-102">\<namedCaches >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="3eee3-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="3eee3-103">Spécifie une collection de paramètres de configuration pour <xref:System.Runtime.Caching.MemoryCache> les instances nommées.</span><span class="sxs-lookup"><span data-stu-id="3eee3-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="3eee3-104">La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration d' `namedCaches` un ou de plusieurs éléments du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3eee3-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="3eee3-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eee3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3eee3-106">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3eee3-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="3eee3-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3eee3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="3eee3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> namedCaches**</span><span class="sxs-lookup"><span data-stu-id="3eee3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eee3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eee3-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="3eee3-110">Type</span><span class="sxs-lookup"><span data-stu-id="3eee3-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eee3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3eee3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3eee3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3eee3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eee3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="3eee3-113">Attributes</span></span>  
  
|<span data-ttu-id="3eee3-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="3eee3-114">Attribute</span></span>|<span data-ttu-id="3eee3-115">Description</span><span class="sxs-lookup"><span data-stu-id="3eee3-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="3eee3-116">Valeur entière qui spécifie la taille maximale autorisée, en mégaoctets, qu’une instance de <xref:System.Runtime.Caching.MemoryCache> peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="3eee3-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="3eee3-117">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="3eee3-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="3eee3-118">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="3eee3-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="3eee3-119">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache.</span><span class="sxs-lookup"><span data-stu-id="3eee3-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="3eee3-120">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="3eee3-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="3eee3-121">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="3eee3-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="3eee3-122">Cette valeur est entrée au format « HH : MM : SS ».</span><span class="sxs-lookup"><span data-stu-id="3eee3-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eee3-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3eee3-123">Child Elements</span></span>  
  
|<span data-ttu-id="3eee3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3eee3-124">Element</span></span>|<span data-ttu-id="3eee3-125">Description</span><span class="sxs-lookup"><span data-stu-id="3eee3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eee3-126">\<add></span><span class="sxs-lookup"><span data-stu-id="3eee3-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="3eee3-127">Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="3eee3-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="3eee3-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="3eee3-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="3eee3-129">Efface la collection `namedCaches` pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="3eee3-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="3eee3-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="3eee3-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="3eee3-131">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="3eee3-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3eee3-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3eee3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="3eee3-133">Élément</span><span class="sxs-lookup"><span data-stu-id="3eee3-133">Element</span></span>|<span data-ttu-id="3eee3-134">Description</span><span class="sxs-lookup"><span data-stu-id="3eee3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eee3-135">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3eee3-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="3eee3-136">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3eee3-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="3eee3-137">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="3eee3-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="3eee3-138">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="3eee3-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="3eee3-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3eee3-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="3eee3-140">Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3eee3-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eee3-141">Notes</span><span class="sxs-lookup"><span data-stu-id="3eee3-141">Remarks</span></span>  
 <span data-ttu-id="3eee3-142">La section de configuration du cache mémoire du fichier Web. config peut `add`contenir `remove`des attributs `clear` , et pour `namedCaches` la collection.</span><span class="sxs-lookup"><span data-stu-id="3eee3-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="3eee3-143">Chaque `namedCaches` entrée est identifiée de manière unique `name` par l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3eee3-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="3eee3-144">Vous pouvez récupérer des instances des entrées de cache mémoire en référençant les informations dans les fichiers de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="3eee3-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="3eee3-145">Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3eee3-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="3eee3-146">L’instance de cache par défaut est l’instance retournée par <xref:System.Runtime.Caching.MemoryCache.Default%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="3eee3-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="3eee3-147">Si vous affectez à l’attribut Name la valeur « default », l’élément utilise l’instance de cache mémoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="3eee3-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eee3-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="3eee3-148">Example</span></span>  
 <span data-ttu-id="3eee3-149">L’exemple suivant montre comment affecter le nom d’entrée de cache par défaut au nom du cache en affectant `name` à l’attribut la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="3eee3-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="3eee3-150">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="3eee3-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="3eee3-151">La définition de ces attributs sur zéro signifie que les heuristiques de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="3eee3-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="3eee3-152">L’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="3eee3-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eee3-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eee3-153">See also</span></span>

- [<span data-ttu-id="3eee3-154">\<memoryCache >, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="3eee3-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
