---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659031"
---
# <a name="add-element-for-namedcaches"></a>\<Ajouter > élément pour \<namedCaches >
Ajoute une `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) à laquelle une instance de <xref:System.Runtime.Caching.MemoryCache> peut croître. La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.|  
|`Name`|Nom du cache.|  
|`PhysicalMemoryLimitPercentage`|Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache. La valeur par défaut est 0, ce qui signifie <xref:System.Runtime.Caching.MemoryCache> que les heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.|  
|`PollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est entrée au format «HH: MM: SS».|  
  
### <a name="child-elements"></a>Éléments enfants  
 `None`  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour les <xref:System.Runtime.Caching.MemoryCache> instances nommées.|  
  
## <a name="remarks"></a>Notes  
 L' `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire. Vous pouvez utiliser l’élément [Clear](clear-element-for-namedcaches.md) avant d’utiliser l' `add` élément pour être certain qu’il n’y a pas d’autres caches nommés dans la collection. Cet élément peut être utilisé dans le fichier machine. config et dans le fichier Web. config.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir les paramètres de l’entrée `namedCache` par défaut de `namedCaches` la collection pour un cache mémoire.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [\<namedCaches >, élément (paramètres de cache)](namedcaches-element-cache-settings.md)
