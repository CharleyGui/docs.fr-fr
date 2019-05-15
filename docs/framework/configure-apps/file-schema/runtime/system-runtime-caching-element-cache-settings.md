---
title: <system.runtime.caching>, élément (paramètres de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a17e8f30c15e98a350ef558cc1cb6ddf65cade
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584508"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System.Runtime.Caching >, élément (paramètres de Cache)
Fournit la configuration pour l’implémentation de <xref:System.Runtime.Caching.ObjectCache> en mémoire par défaut via l’entrée `memoryCache` dans le fichier de configuration.  
  
 \<configuration>  
\<system.runtime.caching>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 `None`  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration qui est utilisé par le common language runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
 Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` . Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Les fonctionnalités et les types de mise en cache en sortie dans l’espace de noms <xref:System.Runtime.Caching> sont nouveaux dans [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> . L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire. Le nom du cache est défini sur le nom de l’entrée du cache par défaut en définissant l’attribut `name` sur « default ».  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro. La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut. L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.  
  
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

- [\<memoryCache >, élément (paramètres de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
