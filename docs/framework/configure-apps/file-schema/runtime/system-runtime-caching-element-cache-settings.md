---
title: <system.runtime.caching>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153852"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="e42bc-102">\<system.runtime.caching> Element (Cache Paramètres)</span><span class="sxs-lookup"><span data-stu-id="e42bc-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="e42bc-103">Fournit la configuration pour l’implémentation de <xref:System.Runtime.Caching.ObjectCache> en mémoire par défaut via l’entrée `memoryCache` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e42bc-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="e42bc-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e42bc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e42bc-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span><span class="sxs-lookup"><span data-stu-id="e42bc-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e42bc-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e42bc-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e42bc-107">Attributes and Elements</span></span>

<span data-ttu-id="e42bc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e42bc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e42bc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e42bc-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="e42bc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e42bc-110">Child Elements</span></span>

|<span data-ttu-id="e42bc-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e42bc-111">Element</span></span>|<span data-ttu-id="e42bc-112">Description</span><span class="sxs-lookup"><span data-stu-id="e42bc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e42bc-113">\<mémoireCache></span><span class="sxs-lookup"><span data-stu-id="e42bc-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="e42bc-114">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="e42bc-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e42bc-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e42bc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e42bc-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e42bc-116">Element</span></span>|<span data-ttu-id="e42bc-117">Description</span><span class="sxs-lookup"><span data-stu-id="e42bc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e42bc-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e42bc-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="e42bc-119">Spécifie l’élément racine de chaque fichier de configuration utilisé par les applications ordinaires de l’exécution de la langue et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e42bc-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e42bc-120">Notes </span><span class="sxs-lookup"><span data-stu-id="e42bc-120">Remarks</span></span>

<span data-ttu-id="e42bc-121">Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="e42bc-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="e42bc-122">Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e42bc-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e42bc-123">La fonctionnalité de mise en <xref:System.Runtime.Caching> cache de sortie et les types dans l’espace de nom sont nouveaux dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e42bc-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42bc-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e42bc-124">Example</span></span>

<span data-ttu-id="e42bc-125">L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="e42bc-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="e42bc-126">L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="e42bc-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="e42bc-127">Le nom du cache est réglé sur le `name` nom d’entrée de cache par défaut en définissant l’attribut à "Default".</span><span class="sxs-lookup"><span data-stu-id="e42bc-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="e42bc-128">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="e42bc-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="e42bc-129">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="e42bc-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="e42bc-130">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="e42bc-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e42bc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e42bc-131">See also</span></span>

- [<span data-ttu-id="e42bc-132">\<memoryCache> Element (Cache Paramètres)</span><span class="sxs-lookup"><span data-stu-id="e42bc-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
