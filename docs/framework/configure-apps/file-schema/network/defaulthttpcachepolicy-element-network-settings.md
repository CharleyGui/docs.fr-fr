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
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088417"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="03ab8-102">\<defaultHttpCachePolicy>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="03ab8-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="03ab8-103">Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="03ab8-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="03ab8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03ab8-104">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03ab8-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="03ab8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="03ab8-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="03ab8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03ab8-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="03ab8-107">Attributes</span></span>  
  
|<span data-ttu-id="03ab8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="03ab8-108">Attribute</span></span>|<span data-ttu-id="03ab8-109">Description</span><span class="sxs-lookup"><span data-stu-id="03ab8-109">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="03ab8-110">Spécifie l’intervalle de temps maximal avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="03ab8-110">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="03ab8-111">Spécifie la durée maximale après le temps d’actualisation calculé avant qu’un objet mis en cache soit marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="03ab8-111">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="03ab8-112">Spécifie la durée minimale pendant laquelle un objet mis en cache est considéré comme actualisé.</span><span class="sxs-lookup"><span data-stu-id="03ab8-112">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="03ab8-113">Spécifie si la stratégie de mise en cache est automatique ou si le cache est contourné.</span><span class="sxs-lookup"><span data-stu-id="03ab8-113">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="03ab8-114">La valeur par défaut est `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="03ab8-114">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03ab8-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="03ab8-115">Child Elements</span></span>  
 <span data-ttu-id="03ab8-116">Aucune</span><span class="sxs-lookup"><span data-stu-id="03ab8-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03ab8-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="03ab8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="03ab8-118">Élément</span><span class="sxs-lookup"><span data-stu-id="03ab8-118">Element</span></span>|<span data-ttu-id="03ab8-119">Description</span><span class="sxs-lookup"><span data-stu-id="03ab8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03ab8-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="03ab8-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="03ab8-121">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="03ab8-121">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03ab8-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="03ab8-122">Remarks</span></span>  
 <span data-ttu-id="03ab8-123">La valeur de l' `policyLevel` attribut est `BypassCache` ou `Default` .</span><span class="sxs-lookup"><span data-stu-id="03ab8-123">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="03ab8-124">Les valeurs des `maximumAge` `maximumStale` éléments, et `minimumFresh` sont soit un intervalle de temps explicite avec un format *d*.\* HH*:*mm*:*SS\* (jours, heures, minutes et secondes), ou les constantes `minValue` ou `maxValue` , selon le cas.</span><span class="sxs-lookup"><span data-stu-id="03ab8-124">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03ab8-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="03ab8-125">Configuration Files</span></span>  
 <span data-ttu-id="03ab8-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="03ab8-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ab8-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="03ab8-127">Example</span></span>  
 <span data-ttu-id="03ab8-128">L’exemple suivant montre comment spécifier une heure de nouvelle actualisation minimale de six heures, une durée d’ancienneté maximale de deux jours et une durée d’obsolescence maximale de quatre heures.</span><span class="sxs-lookup"><span data-stu-id="03ab8-128">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03ab8-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03ab8-129">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="03ab8-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="03ab8-130">Network Settings Schema</span></span>](index.md)
