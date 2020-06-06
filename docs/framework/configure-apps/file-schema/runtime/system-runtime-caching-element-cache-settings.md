---
title: <system.runtime.caching>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153852"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="b855c-102">\<system.runtime.caching>, élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="b855c-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="b855c-103">Fournit la configuration pour l’implémentation de <xref:System.Runtime.Caching.ObjectCache> en mémoire par défaut via l’entrée `memoryCache` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b855c-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="b855c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b855c-104">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b855c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b855c-105">Attributes and Elements</span></span>

<span data-ttu-id="b855c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b855c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b855c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b855c-107">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="b855c-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b855c-108">Child Elements</span></span>

|<span data-ttu-id="b855c-109">Élément</span><span class="sxs-lookup"><span data-stu-id="b855c-109">Element</span></span>|<span data-ttu-id="b855c-110">Description</span><span class="sxs-lookup"><span data-stu-id="b855c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="b855c-111">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="b855c-111">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b855c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b855c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="b855c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b855c-113">Element</span></span>|<span data-ttu-id="b855c-114">Description</span><span class="sxs-lookup"><span data-stu-id="b855c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="b855c-115">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b855c-115">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b855c-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="b855c-116">Remarks</span></span>

<span data-ttu-id="b855c-117">Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="b855c-117">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="b855c-118">Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b855c-118">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b855c-119">Les fonctionnalités et les types de mise en cache de sortie dans l' <xref:System.Runtime.Caching> espace de noms sont nouveaux dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b855c-119">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b855c-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="b855c-120">Example</span></span>

<span data-ttu-id="b855c-121">L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="b855c-121">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="b855c-122">L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="b855c-122">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="b855c-123">Le nom du cache est défini sur le nom de l’entrée de cache par défaut en affectant à l’attribut la valeur `name` « default ».</span><span class="sxs-lookup"><span data-stu-id="b855c-123">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="b855c-124">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="b855c-124">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="b855c-125">La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="b855c-125">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="b855c-126">L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="b855c-126">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b855c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b855c-127">See also</span></span>

- [<span data-ttu-id="b855c-128">\<memoryCache>, Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="b855c-128">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
