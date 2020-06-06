---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154503"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="2c81e-102">\<add>, élément de \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="2c81e-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="2c81e-103">Ajoute une `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="2c81e-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2c81e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c81e-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="2c81e-105">Type</span><span class="sxs-lookup"><span data-stu-id="2c81e-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c81e-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2c81e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2c81e-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2c81e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c81e-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2c81e-108">Attributes</span></span>  
  
|<span data-ttu-id="2c81e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2c81e-109">Attribute</span></span>|<span data-ttu-id="2c81e-110">Description</span><span class="sxs-lookup"><span data-stu-id="2c81e-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="2c81e-111">Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) à laquelle une instance de <xref:System.Runtime.Caching.MemoryCache> peut croître.</span><span class="sxs-lookup"><span data-stu-id="2c81e-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="2c81e-112">La valeur par défaut est 0, ce qui signifie que les <xref:System.Runtime.Caching.MemoryCache> heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="2c81e-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="2c81e-113">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="2c81e-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="2c81e-114">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache.</span><span class="sxs-lookup"><span data-stu-id="2c81e-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="2c81e-115">La valeur par défaut est 0, ce qui signifie que les <xref:System.Runtime.Caching.MemoryCache> heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="2c81e-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="2c81e-116">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="2c81e-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="2c81e-117">Cette valeur est entrée au format « HH : MM : SS ».</span><span class="sxs-lookup"><span data-stu-id="2c81e-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c81e-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2c81e-118">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="2c81e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2c81e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c81e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="2c81e-120">Element</span></span>|<span data-ttu-id="2c81e-121">Description</span><span class="sxs-lookup"><span data-stu-id="2c81e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="2c81e-122">Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.</span><span class="sxs-lookup"><span data-stu-id="2c81e-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c81e-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c81e-123">Remarks</span></span>  
 <span data-ttu-id="2c81e-124">L' `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="2c81e-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="2c81e-125">Vous pouvez utiliser l’élément [Clear](clear-element-for-namedcaches.md) avant d’utiliser l' `add` élément pour être certain qu’il n’y a pas d’autres caches nommés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="2c81e-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="2c81e-126">Cet élément peut être utilisé dans le fichier machine. config et dans le fichier Web. config.</span><span class="sxs-lookup"><span data-stu-id="2c81e-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c81e-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="2c81e-127">Example</span></span>  
 <span data-ttu-id="2c81e-128">L’exemple suivant montre comment définir les paramètres de l’entrée par défaut de `namedCache` la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="2c81e-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c81e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c81e-129">See also</span></span>

- [<span data-ttu-id="2c81e-130">\<namedCaches>, Élément (paramètres de cache)</span><span class="sxs-lookup"><span data-stu-id="2c81e-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
