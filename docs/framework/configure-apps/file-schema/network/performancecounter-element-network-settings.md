---
title: <performanceCounter>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283090"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter >, élément (paramètres réseau)
Active ou désactive les compteurs de performance réseau.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**performanceCounters >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Spécifie si les compteurs de performance réseau sont activés. La valeur par défaut est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Paramètres](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
 Les compteurs de performance réseau doivent être activés dans le fichier de configuration pour pouvoir être utilisés. L'ensemble des compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration. Il n'est pas possible d'activer ou de désactiver ces compteurs de manière individuelle. Pour plus d’informations sur les compteurs de performances de mise en réseau spécifiques, consultez [compteurs de performances de mise en réseau](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).  
  
 La valeur par défaut est que les compteurs de performance réseau sont désactivés.  
  
 La propriété <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> peut être utilisée pour récupérer la valeur actuelle de l’attribut **activé** à partir des fichiers de configuration applicables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer les <xref:System.Net> et les espaces de noms associés pour activer les compteurs de performances de mise en réseau.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
- [Compteurs de performances de mise en réseau](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
