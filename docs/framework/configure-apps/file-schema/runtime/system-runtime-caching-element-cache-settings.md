---
title: <system.runtime.caching>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115505"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="f78c5-102">\<l’élément System. Runtime. Caching > (paramètres du cache)</span><span class="sxs-lookup"><span data-stu-id="f78c5-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="f78c5-103">Fournit la configuration pour l’implémentation de <xref:System.Runtime.Caching.ObjectCache> en mémoire par défaut via l’entrée `memoryCache` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f78c5-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="f78c5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f78c5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f78c5-105">&nbsp;&nbsp; **\<System. Runtime. caching >**</span><span class="sxs-lookup"><span data-stu-id="f78c5-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78c5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f78c5-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f78c5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f78c5-107">Attributes and Elements</span></span>

<span data-ttu-id="f78c5-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f78c5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f78c5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f78c5-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="f78c5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f78c5-110">Child Elements</span></span>

|<span data-ttu-id="f78c5-111">Élément</span><span class="sxs-lookup"><span data-stu-id="f78c5-111">Element</span></span>|<span data-ttu-id="f78c5-112">Description</span><span class="sxs-lookup"><span data-stu-id="f78c5-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f78c5-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="f78c5-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="f78c5-114">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f78c5-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f78c5-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f78c5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f78c5-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f78c5-116">Element</span></span>|<span data-ttu-id="f78c5-117">Description</span><span class="sxs-lookup"><span data-stu-id="f78c5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f78c5-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f78c5-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="f78c5-119">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f78c5-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f78c5-120">Notes</span><span class="sxs-lookup"><span data-stu-id="f78c5-120">Remarks</span></span>

<span data-ttu-id="f78c5-121">Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="f78c5-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="f78c5-122">Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f78c5-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f78c5-123">Les fonctionnalités et les types de mise en cache de sortie dans l’espace de noms <xref:System.Runtime.Caching> sont nouveaux dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f78c5-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f78c5-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f78c5-124">Example</span></span>

<span data-ttu-id="f78c5-125">L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f78c5-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="f78c5-126">L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="f78c5-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="f78c5-127">Le nom du cache est défini sur le nom de l’entrée de cache par défaut en affectant à l’attribut `name` la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="f78c5-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="f78c5-128">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="f78c5-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="f78c5-129">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f78c5-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="f78c5-130">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="f78c5-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f78c5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f78c5-131">See also</span></span>

- [<span data-ttu-id="f78c5-132">Élément \<memoryCache > (paramètres du cache)</span><span class="sxs-lookup"><span data-stu-id="f78c5-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
