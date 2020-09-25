---
title: <memoryCache>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 14480682c5d221216df5da3844897855d1d92a0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192423"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache>, élément (paramètres de cache)

Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> . La classe <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> définit un élément [memoryCache](memorycache-element-cache-settings.md) que vous pouvez utiliser pour configurer le cache. Vous pouvez utiliser plusieurs instances de la classe <xref:System.Runtime.Caching.MemoryCache> dans une même application. Chaque élément `memoryCache` dans le fichier de configuration peut contenir des paramètres pour une instance <xref:System.Runtime.Caching.MemoryCache> nommée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Type  

 Classe<xref:System.Runtime.Caching.MemoryCache> .  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Taille de mémoire maximale, en mégaoctets, que peut atteindre une instance d’un objet <xref:System.Runtime.Caching.MemoryCache> . La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`Name`|Nom de la configuration du cache.|  
|`PhysicalMemoryLimitPercentage`|Pourcentage de mémoire physique pouvant être utilisé par le cache. La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`PollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. La valeur est entrée au format « HH:MM:SS ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour l’instance `namedCache` .|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au .NET Framework.|  
  
## <a name="remarks"></a>Notes  

 La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation concrète de la classe <xref:System.Runtime.Caching.ObjectCache> abstraite. Les instances de la classe <xref:System.Runtime.Caching.MemoryCache> peuvent être fournies avec les informations de configuration tirées des fichiers de configuration d’application. La section de configuration [memoryCache](memorycache-element-cache-settings.md) contient une collection de configurations `namedCaches` .  
  
 Quand un objet cache en mémoire est initialisé, il essaie tout d’abord de trouver une entrée `namedCaches` qui correspond au nom mentionné dans le paramètre passé au constructeur du cache mémoire. S’il trouve une entrée `namedCaches` , les informations de gestion de la mémoire et d’interrogation sont récupérées à partir du fichier de configuration.  
  
 Le processus d’initialisation détermine ensuite si des entrées de configuration ont été substituées, en utilisant la collection facultative de paires nom/valeur d’informations de configuration dans le constructeur. Si vous passez l’une des valeurs suivantes dans la collection de paires nom/valeur, ces valeurs remplacent les informations obtenues à partir du fichier de configuration :  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment définir le nom de l' <xref:System.Runtime.Caching.MemoryCache> objet dans le cache par défaut en affectant à l' `name` attribut la valeur « default ».  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryLimitPercentage` sont définis sur zéro. La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut. L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Caching.MemoryCache>
- [\<system.runtime.caching> , Élément (paramètres de cache)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches> , Élément (paramètres de cache)](namedcaches-element-cache-settings.md)
