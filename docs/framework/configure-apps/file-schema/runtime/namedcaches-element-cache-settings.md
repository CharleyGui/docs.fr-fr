---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153956"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="02392-102">\<nomméCaches> Element (Cache Paramètres)</span><span class="sxs-lookup"><span data-stu-id="02392-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="02392-103">Spécifie une collection de <xref:System.Runtime.Caching.MemoryCache> paramètres de configuration pour les instances nommées.</span><span class="sxs-lookup"><span data-stu-id="02392-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="02392-104">La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la `namedCaches` collecte des paramètres de configuration à partir d’un ou de plusieurs éléments du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="02392-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="02392-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="02392-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02392-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="02392-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="02392-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mémoireCache>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="02392-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="02392-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nomméCaches>**</span><span class="sxs-lookup"><span data-stu-id="02392-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02392-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02392-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="02392-110">Type</span><span class="sxs-lookup"><span data-stu-id="02392-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02392-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="02392-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02392-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="02392-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02392-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="02392-113">Attributes</span></span>  
  
|<span data-ttu-id="02392-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="02392-114">Attribute</span></span>|<span data-ttu-id="02392-115">Description</span><span class="sxs-lookup"><span data-stu-id="02392-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="02392-116">Une valeur integer qui spécifie la taille maximale autorisée, <xref:System.Runtime.Caching.MemoryCache> dans les mégaoctets, qu’une instance d’un peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="02392-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="02392-117">La valeur par défaut est de 0, ce qui <xref:System.Runtime.Caching.MemoryCache> signifie que les heuristiques autosizing de la classe sont utilisés par défaut.</span><span class="sxs-lookup"><span data-stu-id="02392-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="02392-118">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="02392-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="02392-119">Une valeur d’intégrant entre 0 et 100 qui spécifie le pourcentage maximum de mémoire d’ordinateur physiquement installée qui peut être consommée par le cache.</span><span class="sxs-lookup"><span data-stu-id="02392-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="02392-120">La valeur par défaut est de 0, ce qui <xref:System.Runtime.Caching.MemoryCache> signifie que les heuristiques autosizing de la classe sont utilisés par défaut.</span><span class="sxs-lookup"><span data-stu-id="02392-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="02392-121">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="02392-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="02392-122">Cette valeur est saisie dans le format "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="02392-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02392-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="02392-123">Child Elements</span></span>  
  
|<span data-ttu-id="02392-124">Élément</span><span class="sxs-lookup"><span data-stu-id="02392-124">Element</span></span>|<span data-ttu-id="02392-125">Description</span><span class="sxs-lookup"><span data-stu-id="02392-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02392-126">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="02392-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="02392-127">Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="02392-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="02392-128">\<clair></span><span class="sxs-lookup"><span data-stu-id="02392-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="02392-129">Efface la collection `namedCaches` pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="02392-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="02392-130">\<supprimer></span><span class="sxs-lookup"><span data-stu-id="02392-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="02392-131">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="02392-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02392-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="02392-132">Parent Elements</span></span>  
  
|<span data-ttu-id="02392-133">Élément</span><span class="sxs-lookup"><span data-stu-id="02392-133">Element</span></span>|<span data-ttu-id="02392-134">Description</span><span class="sxs-lookup"><span data-stu-id="02392-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02392-135">\<configuration></span><span class="sxs-lookup"><span data-stu-id="02392-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="02392-136">Spécifie l’élément racine de chaque fichier de configuration utilisé par les applications ordinaires de l’exécution de la langue et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02392-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="02392-137">\<mémoireCache></span><span class="sxs-lookup"><span data-stu-id="02392-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="02392-138">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="02392-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="02392-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="02392-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="02392-140">Contient des types qui vous permettent de mettre en œuvre la mise en cache de sortie dans les applications qui sont intégrées dans le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="02392-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02392-141">Notes </span><span class="sxs-lookup"><span data-stu-id="02392-141">Remarks</span></span>  
 <span data-ttu-id="02392-142">La section de configuration de cache mémoire `add`du `remove`fichier `clear` Web.config peut contenir, et les attributs pour la `namedCaches` collection.</span><span class="sxs-lookup"><span data-stu-id="02392-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="02392-143">Chaque `namedCaches` entrée est identifiée `name` de façon unique par l’attribut.</span><span class="sxs-lookup"><span data-stu-id="02392-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="02392-144">Vous pouvez récupérer des instances d’entrées de cache de mémoire en faisant référence aux informations contenues dans les fichiers de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="02392-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="02392-145">Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="02392-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="02392-146">L’instance de cache par défaut <xref:System.Runtime.Caching.MemoryCache.Default%2A> est l’instance qui est retournée de la propriété.</span><span class="sxs-lookup"><span data-stu-id="02392-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="02392-147">Si vous définissez l’attribut de nom en « par défaut », l’élément utilise l’instance de cache de mémoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="02392-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02392-148"> Exemple</span><span class="sxs-lookup"><span data-stu-id="02392-148">Example</span></span>  
 <span data-ttu-id="02392-149">L’exemple suivant montre comment définir le nom du cache au `name` nom d’entrée de cache par défaut en définissant l’attribut en « par défaut ».</span><span class="sxs-lookup"><span data-stu-id="02392-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="02392-150">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="02392-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="02392-151">Définir ces attributs à zéro signifie que les heuristiques autosérisantes de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="02392-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="02392-152">L’implémentation du cache compare la charge mémoire actuelle aux limites de mémoire absolues et basées sur le pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="02392-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02392-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02392-153">See also</span></span>

- [<span data-ttu-id="02392-154">\<memoryCache> Element (Cache Paramètres)</span><span class="sxs-lookup"><span data-stu-id="02392-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
