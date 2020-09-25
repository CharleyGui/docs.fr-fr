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
ms.openlocfilehash: 4120c57fbb65da1c124414cbe9cfba7ae64388f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190317"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<defaultHttpCachePolicy>, élément (paramètres réseau)

Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maximumAge`|Spécifie l’intervalle de temps maximal avant qu’un objet mis en cache soit marqué comme ayant expiré.|  
|`maximumStale`|Spécifie la durée maximale après le temps d’actualisation calculé avant qu’un objet mis en cache soit marqué comme ayant expiré.|  
|`minimumFresh`|Spécifie la durée minimale pendant laquelle un objet mis en cache est considéré comme actualisé.|  
|`policyLevel`|Spécifie si la stratégie de mise en cache est automatique ou si le cache est contourné. La valeur par défaut est `BypassCache`.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
  
## <a name="remarks"></a>Notes  

 La valeur de l' `policyLevel` attribut est `BypassCache` ou `Default` .  
  
 Les valeurs des `maximumAge` `maximumStale` éléments, et `minimumFresh` sont soit un intervalle de temps explicite avec un format *d*.* HH*:*mm*:*SS* (jours, heures, minutes et secondes), ou les constantes `minValue` ou `maxValue` , selon le cas.  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment spécifier une heure de nouvelle actualisation minimale de six heures, une durée d’ancienneté maximale de deux jours et une durée d’obsolescence maximale de quatre heures.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma des paramètres réseau](index.md)
