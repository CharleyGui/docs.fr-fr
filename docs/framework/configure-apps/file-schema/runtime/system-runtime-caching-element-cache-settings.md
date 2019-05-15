---
title: <system.runtime.caching>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a17e8f30c15e98a350ef558cc1cb6ddf65cade
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584508"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="f04fb-102">\<System.Runtime.Caching >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="f04fb-102">\<system.runtime.caching> Element (Cache Settings)</span></span>
<span data-ttu-id="f04fb-103">Fournit la configuration pour l’implémentation de <xref:System.Runtime.Caching.ObjectCache> en mémoire par défaut via l’entrée `memoryCache` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f04fb-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="f04fb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f04fb-104">\<configuration></span></span>  
<span data-ttu-id="f04fb-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="f04fb-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f04fb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f04fb-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f04fb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f04fb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f04fb-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f04fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f04fb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f04fb-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="f04fb-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f04fb-110">Child Elements</span></span>  
  
|<span data-ttu-id="f04fb-111">Élément</span><span class="sxs-lookup"><span data-stu-id="f04fb-111">Element</span></span>|<span data-ttu-id="f04fb-112">Description</span><span class="sxs-lookup"><span data-stu-id="f04fb-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f04fb-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="f04fb-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="f04fb-114">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f04fb-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f04fb-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f04fb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f04fb-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f04fb-116">Element</span></span>|<span data-ttu-id="f04fb-117">Description</span><span class="sxs-lookup"><span data-stu-id="f04fb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f04fb-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f04fb-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f04fb-119">Spécifie l’élément racine dans chaque fichier de configuration qui est utilisé par le common language runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f04fb-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f04fb-120">Notes</span><span class="sxs-lookup"><span data-stu-id="f04fb-120">Remarks</span></span>  
 <span data-ttu-id="f04fb-121">Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="f04fb-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="f04fb-122">Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f04fb-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f04fb-123">Les fonctionnalités et les types de mise en cache en sortie dans l’espace de noms <xref:System.Runtime.Caching> sont nouveaux dans [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f04fb-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="f04fb-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f04fb-124">Example</span></span>  
 <span data-ttu-id="f04fb-125">L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="f04fb-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="f04fb-126">L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="f04fb-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="f04fb-127">Le nom du cache est défini sur le nom de l’entrée du cache par défaut en définissant l’attribut `name` sur « default ».</span><span class="sxs-lookup"><span data-stu-id="f04fb-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="f04fb-128">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="f04fb-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="f04fb-129">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f04fb-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="f04fb-130">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="f04fb-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f04fb-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f04fb-131">See also</span></span>

- [<span data-ttu-id="f04fb-132">\<memoryCache >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="f04fb-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
