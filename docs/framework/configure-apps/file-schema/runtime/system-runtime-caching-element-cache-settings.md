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
ms.openlocfilehash: 91a97807d45d3cafdac0c0608dc9590533b185dc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663430"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System. Runtime. Caching >, élément (paramètres de cache)

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
|[\<memoryCache>](memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.|  
  
## <a name="remarks"></a>Notes

Les classes de cet espace de noms fournissent un moyen d’utiliser des fonctionnalités de mise en cache comme celles d’ASP.NET, mais sans dépendance de l’assembly `System.Web` . Pour plus d'informations, consultez [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Les fonctionnalités et les types de mise en <xref:System.Runtime.Caching> cache de sortie dans l’espace de noms sont nouveaux dans .NET Framework 4.  
  
## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> . L’exemple montre comment configurer une instance de l’entrée `namedCaches` pour le cache mémoire. Le nom du cache est défini sur le nom de l’entrée de cache par défaut `name` en affectant à l’attribut la valeur «default».  
  
Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro. La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut. L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.  
  
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

- [\<memoryCache >, élément (paramètres de cache)](memorycache-element-cache-settings.md)
