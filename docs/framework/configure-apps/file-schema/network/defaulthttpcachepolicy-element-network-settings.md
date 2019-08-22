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
ms.openlocfilehash: 1dd31884a072d16ed004c0b49be61e8cee399787
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664151"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="826be-102">\<defaultHttpCachePolicy >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="826be-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="826be-103">Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="826be-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="826be-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="826be-104">\<configuration></span></span>  
<span data-ttu-id="826be-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="826be-105">\<system.net></span></span>  
<span data-ttu-id="826be-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="826be-106">\<requestCaching></span></span>  
<span data-ttu-id="826be-107">\<defaultHttpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="826be-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826be-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="826be-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="826be-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="826be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="826be-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="826be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="826be-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="826be-111">Attributes</span></span>  
  
|<span data-ttu-id="826be-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="826be-112">Attribute</span></span>|<span data-ttu-id="826be-113">Description</span><span class="sxs-lookup"><span data-stu-id="826be-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="826be-114">Spécifie l’intervalle de temps maximal avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="826be-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="826be-115">Spécifie la durée maximale après le temps d’actualisation calculé avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="826be-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="826be-116">Spécifie la durée minimale pendant laquelle un objet mis en cache est considéré comme actualisé.</span><span class="sxs-lookup"><span data-stu-id="826be-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="826be-117">Spécifie si la stratégie de mise en cache est automatique ou si le cache est contourné.</span><span class="sxs-lookup"><span data-stu-id="826be-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="826be-118">La valeur par défaut est `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="826be-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="826be-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="826be-119">Child Elements</span></span>  
 <span data-ttu-id="826be-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="826be-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="826be-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="826be-121">Parent Elements</span></span>  
  
|<span data-ttu-id="826be-122">Élément</span><span class="sxs-lookup"><span data-stu-id="826be-122">Element</span></span>|<span data-ttu-id="826be-123">Description</span><span class="sxs-lookup"><span data-stu-id="826be-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="826be-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="826be-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="826be-125">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="826be-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="826be-126">Notes</span><span class="sxs-lookup"><span data-stu-id="826be-126">Remarks</span></span>  
 <span data-ttu-id="826be-127">La valeur de l' `policyLevel` attribut `BypassCache` est ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="826be-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="826be-128">Les `maximumAge`valeurs des éléments `maximumStale`, et `minimumFresh` sont soit un intervalle de temps explicite avec un format *d*. *HH*:*mm*:*SS* (jours, heures, minutes et secondes), `minValue` ou les constantes ou `maxValue`, selon le cas.</span><span class="sxs-lookup"><span data-stu-id="826be-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="826be-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="826be-129">Configuration Files</span></span>  
 <span data-ttu-id="826be-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="826be-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="826be-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="826be-131">Example</span></span>  
 <span data-ttu-id="826be-132">L’exemple suivant montre comment spécifier une heure de nouvelle actualisation minimale de six heures, une durée d’ancienneté maximale de deux jours et une durée d’obsolescence maximale de quatre heures.</span><span class="sxs-lookup"><span data-stu-id="826be-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="826be-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="826be-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="826be-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="826be-134">Network Settings Schema</span></span>](index.md)
