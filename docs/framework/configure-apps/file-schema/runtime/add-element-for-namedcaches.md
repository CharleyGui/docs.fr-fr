---
title: Élément <add> pour <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154503"
---
# <a name="add-element-for-namedcaches"></a>\<ajouter> Element pour \<namedCaches>
Ajoute `namedCache` une entrée `namedCaches` à la collection pour un cache mémoire.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mémoireCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nomméCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**  
  
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
|`CacheMemoryLimitMegabytes`|Une valeur d’intégrant qui spécifie la taille maximale <xref:System.Runtime.Caching.MemoryCache> autorisée (dans les mégaoctets) qu’une instance d’un peut atteindre. La valeur par défaut est de <xref:System.Runtime.Caching.MemoryCache> 0, ce qui signifie que les heuristiques autosizing de la classe sont utilisées par défaut.|  
|`Name`|Nom du cache.|  
|`PhysicalMemoryLimitPercentage`|Une valeur d’intégrant entre 0 et 100 qui spécifie le pourcentage maximum de mémoire d’ordinateur physiquement installée qui peut être consommée par le cache. La valeur par défaut est de <xref:System.Runtime.Caching.MemoryCache> 0, ce qui signifie que les heuristiques autosizing de la classe sont utilisées par défaut.|  
|`PollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est saisie dans le format "HH:MM:SS".|  
  
### <a name="child-elements"></a>Éléments enfants  
 `None`  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<nomméCaches>](namedcaches-element-cache-settings.md)|Contient une collection de paramètres <xref:System.Runtime.Caching.MemoryCache> de configuration pour les instances nommées.|  
  
## <a name="remarks"></a>Notes   
 L’élément `add` ajoute une `namedCaches` entrée à la collection pour un cache mémoire. Vous pouvez [clear](clear-element-for-namedcaches.md) utiliser l’élément `add` clair avant d’utiliser l’élément pour être certain qu’il n’y a pas d’autres caches nommées dans la collection. Cet élément peut être utilisé dans le fichier machine.config et dans le fichier Web.config.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment définir `namedCache` les `namedCaches` paramètres de l’entrée par défaut de la collection pour un cache mémoire.  
  
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

- [\<nomméCaches> Element (Cache Paramètres)](namedcaches-element-cache-settings.md)
