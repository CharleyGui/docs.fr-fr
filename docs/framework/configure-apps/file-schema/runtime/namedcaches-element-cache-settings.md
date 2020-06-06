---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153956"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches>, élément (paramètres de cache)
Spécifie une collection de paramètres de configuration pour les instances nommées <xref:System.Runtime.Caching.MemoryCache> . La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration d’un ou `namedCaches` de plusieurs éléments du fichier de configuration.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
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
|`pollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est entrée au format « HH : MM : SS ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|  
|[\<clear>](clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<remove>](remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.|  
  
## <a name="remarks"></a>Remarques  
 La section de configuration du cache mémoire du fichier Web. config peut contenir des `add` `remove` attributs, et `clear` pour la `namedCaches` collection. Chaque `namedCaches` entrée est identifiée de manière unique par l' `name` attribut.  
  
 Vous pouvez récupérer des instances des entrées de cache mémoire en référençant les informations dans les fichiers de configuration de l’application. Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration. L’instance de cache par défaut est l’instance retournée par la <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriété.  
  
 Si vous affectez à l’attribut Name la valeur « default », l’élément utilise l’instance de cache mémoire par défaut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment affecter le nom d’entrée de cache par défaut au nom du cache en affectant `name` à l’attribut la valeur « default ».  
  
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

- [\<memoryCache>, Élément (paramètres de cache)](memorycache-element-cache-settings.md)
