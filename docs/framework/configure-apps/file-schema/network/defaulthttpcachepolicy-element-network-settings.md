---
title: <defaultHttpCachePolicy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: f3b029e8b931e976bee85c98dd926e020c5b8743
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698279"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="377ea-102">\<defaultHttpCachePolicy >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="377ea-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="377ea-103">Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="377ea-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
[<span data-ttu-id="377ea-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="377ea-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="377ea-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="377ea-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="377ea-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="377ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>  
<span data-ttu-id="377ea-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="377ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377ea-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="377ea-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="377ea-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="377ea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="377ea-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="377ea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="377ea-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="377ea-111">Attributes</span></span>  
  
|<span data-ttu-id="377ea-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="377ea-112">Attribute</span></span>|<span data-ttu-id="377ea-113">Description</span><span class="sxs-lookup"><span data-stu-id="377ea-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="377ea-114">Spécifie l’intervalle de temps maximal avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="377ea-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="377ea-115">Spécifie la durée maximale après le temps d’actualisation calculé avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="377ea-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="377ea-116">Spécifie la durée minimale pendant laquelle un objet mis en cache est considéré comme actualisé.</span><span class="sxs-lookup"><span data-stu-id="377ea-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="377ea-117">Spécifie si la stratégie de mise en cache est automatique ou si le cache est contourné.</span><span class="sxs-lookup"><span data-stu-id="377ea-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="377ea-118">La valeur par défaut est `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="377ea-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="377ea-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="377ea-119">Child Elements</span></span>  
 <span data-ttu-id="377ea-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="377ea-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="377ea-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="377ea-121">Parent Elements</span></span>  
  
|<span data-ttu-id="377ea-122">Élément</span><span class="sxs-lookup"><span data-stu-id="377ea-122">Element</span></span>|<span data-ttu-id="377ea-123">Description</span><span class="sxs-lookup"><span data-stu-id="377ea-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="377ea-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="377ea-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="377ea-125">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="377ea-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="377ea-126">Notes</span><span class="sxs-lookup"><span data-stu-id="377ea-126">Remarks</span></span>  
 <span data-ttu-id="377ea-127">La valeur de l’attribut `policyLevel` est `BypassCache` ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="377ea-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="377ea-128">Les valeurs des éléments `maximumAge`, `maximumStale` et `minimumFresh` sont soit un intervalle de temps explicite avec un format *d*. *hh*:*mm*:*SS* (jours, heures, minutes et secondes), ou les constantes `minValue` ou `maxValue`, selon le cas.</span><span class="sxs-lookup"><span data-stu-id="377ea-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="377ea-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="377ea-129">Configuration Files</span></span>  
 <span data-ttu-id="377ea-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="377ea-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="377ea-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="377ea-131">Example</span></span>  
 <span data-ttu-id="377ea-132">L’exemple suivant montre comment spécifier une heure de nouvelle actualisation minimale de six heures, une durée d’ancienneté maximale de deux jours et une durée d’obsolescence maximale de quatre heures.</span><span class="sxs-lookup"><span data-stu-id="377ea-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="377ea-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="377ea-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="377ea-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="377ea-134">Network Settings Schema</span></span>](index.md)
