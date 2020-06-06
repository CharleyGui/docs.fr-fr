---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153956"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="f2ca6-102">\<namedCaches>, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="f2ca6-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="f2ca6-103">Spécifie une collection de paramètres de configuration pour les instances nommées <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f2ca6-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="f2ca6-104">La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration d’un ou `namedCaches` de plusieurs éléments du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="f2ca6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ca6-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="f2ca6-106">Type</span><span class="sxs-lookup"><span data-stu-id="f2ca6-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2ca6-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f2ca6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f2ca6-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2ca6-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f2ca6-109">Attributes</span></span>  
  
|<span data-ttu-id="f2ca6-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f2ca6-110">Attribute</span></span>|<span data-ttu-id="f2ca6-111">Description</span><span class="sxs-lookup"><span data-stu-id="f2ca6-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="f2ca6-112">Valeur entière qui spécifie la taille maximale autorisée, en mégaoctets, qu’une instance de <xref:System.Runtime.Caching.MemoryCache> peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="f2ca6-113">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="f2ca6-114">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="f2ca6-115">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="f2ca6-116">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="f2ca6-117">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="f2ca6-118">Cette valeur est entrée au format « HH : MM : SS ».</span><span class="sxs-lookup"><span data-stu-id="f2ca6-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2ca6-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f2ca6-119">Child Elements</span></span>  
  
|<span data-ttu-id="f2ca6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f2ca6-120">Element</span></span>|<span data-ttu-id="f2ca6-121">Description</span><span class="sxs-lookup"><span data-stu-id="f2ca6-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="f2ca6-122">Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="f2ca6-123">Efface la collection `namedCaches` pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="f2ca6-124">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2ca6-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f2ca6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f2ca6-126">Élément</span><span class="sxs-lookup"><span data-stu-id="f2ca6-126">Element</span></span>|<span data-ttu-id="f2ca6-127">Description</span><span class="sxs-lookup"><span data-stu-id="f2ca6-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="f2ca6-128">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="f2ca6-129">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f2ca6-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="f2ca6-130">Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2ca6-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2ca6-131">Remarks</span></span>  
 <span data-ttu-id="f2ca6-132">La section de configuration du cache mémoire du fichier Web. config peut contenir des `add` `remove` attributs, et `clear` pour la `namedCaches` collection.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="f2ca6-133">Chaque `namedCaches` entrée est identifiée de manière unique par l' `name` attribut.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="f2ca6-134">Vous pouvez récupérer des instances des entrées de cache mémoire en référençant les informations dans les fichiers de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="f2ca6-135">Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="f2ca6-136">L’instance de cache par défaut est l’instance retournée par la <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="f2ca6-137">Si vous affectez à l’attribut Name la valeur « default », l’élément utilise l’instance de cache mémoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2ca6-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2ca6-138">Example</span></span>  
 <span data-ttu-id="f2ca6-139">L’exemple suivant montre comment affecter le nom d’entrée de cache par défaut au nom du cache en affectant `name` à l’attribut la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="f2ca6-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="f2ca6-140">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="f2ca6-141">La définition de ces attributs sur zéro signifie que les heuristiques de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="f2ca6-142">L’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2ca6-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ca6-143">See also</span></span>

- [<span data-ttu-id="f2ca6-144">\<memoryCache>, Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="f2ca6-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
