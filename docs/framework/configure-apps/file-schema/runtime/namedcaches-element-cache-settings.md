---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663581"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches >, élément (paramètres de cache)
Spécifie une collection de paramètres de configuration pour <xref:System.Runtime.Caching.MemoryCache> les instances nommées. La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration d' `namedCaches` un ou de plusieurs éléments du fichier de configuration.  
  
 \<configuration>  
\< system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Valeur entière qui spécifie la taille maximale autorisée, en mégaoctets, qu’une instance de <xref:System.Runtime.Caching.MemoryCache> peut atteindre. La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.|  
|`name`|Nom du cache.|  
|`physicalMemoryLimitPercentage`|Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire physique installée sur l’ordinateur qui peut être consommé par le cache. La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe est utilisée par défaut.|  
|`pollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est entrée au format «HH: MM: SS».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|  
|[\<clear>](clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<remove>](remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
  
## <a name="remarks"></a>Notes  
 La section de configuration du cache mémoire du fichier Web. config peut `add`contenir `remove`des attributs `clear` , et pour `namedCaches` la collection. Chaque `namedCaches` entrée est identifiée de manière unique `name` par l’attribut.  
  
 Vous pouvez récupérer des instances des entrées de cache mémoire en référençant les informations dans les fichiers de configuration de l’application. Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration. L’instance de cache par défaut est l’instance retournée par <xref:System.Runtime.Caching.MemoryCache.Default%2A> la propriété.  
  
 Si vous affectez à l’attribut Name la valeur «default», l’élément utilise l’instance de cache mémoire par défaut.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment affecter le nom d’entrée de cache par défaut au nom du cache en affectant `name` à l’attribut la valeur «default».  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro. La définition de ces attributs sur zéro signifie que les heuristiques de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées. L’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage toutes les deux minutes.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [\<memoryCache >, élément (paramètres de cache)](memorycache-element-cache-settings.md)
