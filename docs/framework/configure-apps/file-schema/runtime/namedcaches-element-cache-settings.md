---
title: <namedCaches>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153956"
---
# <a name="namedcaches-element-cache-settings"></a>\<nomméCaches> Element (Cache Paramètres)
Spécifie une collection de <xref:System.Runtime.Caching.MemoryCache> paramètres de configuration pour les instances nommées. La <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la `namedCaches` collecte des paramètres de configuration à partir d’un ou de plusieurs éléments du fichier de configuration.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mémoireCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nomméCaches>**  
  
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
|`cacheMemoryLimitMegabytes`|Une valeur integer qui spécifie la taille maximale autorisée, <xref:System.Runtime.Caching.MemoryCache> dans les mégaoctets, qu’une instance d’un peut atteindre. La valeur par défaut est de 0, ce qui <xref:System.Runtime.Caching.MemoryCache> signifie que les heuristiques autosizing de la classe sont utilisés par défaut.|  
|`name`|Nom du cache.|  
|`physicalMemoryLimitPercentage`|Une valeur d’intégrant entre 0 et 100 qui spécifie le pourcentage maximum de mémoire d’ordinateur physiquement installée qui peut être consommée par le cache. La valeur par défaut est de 0, ce qui <xref:System.Runtime.Caching.MemoryCache> signifie que les heuristiques autosizing de la classe sont utilisés par défaut.|  
|`pollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est saisie dans le format "HH:MM:SS".|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter>](add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|  
|[\<clair>](clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<supprimer>](remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine de chaque fichier de configuration utilisé par les applications ordinaires de l’exécution de la langue et .NET Framework.|  
|[\<mémoireCache>](memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Contient des types qui vous permettent de mettre en œuvre la mise en cache de sortie dans les applications qui sont intégrées dans le cadre .NET.|  
  
## <a name="remarks"></a>Notes   
 La section de configuration de cache mémoire `add`du `remove`fichier `clear` Web.config peut contenir, et les attributs pour la `namedCaches` collection. Chaque `namedCaches` entrée est identifiée `name` de façon unique par l’attribut.  
  
 Vous pouvez récupérer des instances d’entrées de cache de mémoire en faisant référence aux informations contenues dans les fichiers de configuration d’application. Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration. L’instance de cache par défaut <xref:System.Runtime.Caching.MemoryCache.Default%2A> est l’instance qui est retournée de la propriété.  
  
 Si vous définissez l’attribut de nom en « par défaut », l’élément utilise l’instance de cache de mémoire par défaut.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment définir le nom du cache au `name` nom d’entrée de cache par défaut en définissant l’attribut en « par défaut ».  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro. Définir ces attributs à zéro signifie que les heuristiques autosérisantes de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées. L’implémentation du cache compare la charge mémoire actuelle aux limites de mémoire absolues et basées sur le pourcentage toutes les deux minutes.  
  
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

- [\<memoryCache> Element (Cache Paramètres)](memorycache-element-cache-settings.md)
