---
title: <settings>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167273"
---
# <a name="settings-element-network-settings"></a>\<settings>, élément (paramètres réseau)

Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Personnalise les paramètres de la demande Web.|  
|[protocoles](ipv6-element-network-settings.md)|Active la prise en charge du protocole IPv6 (Internet Protocol version 6).|  
|[\<performanceCounter> , Élément (paramètres réseau)](performancecounter-element-network-settings.md)|Active les compteurs de performances réseau.|  
|[servicePointManager](servicepointmanager-element-network-settings.md)|Configure les connexions aux ressources réseau.|  
|[socle](socket-element-network-settings.md)|Spécifie si les opérations de socket utilisent des ports de terminaison.|  
|[\<webProxyScript> , Élément (paramètres réseau)](webproxyscript-element-network-settings.md)|Configure les caractéristiques du script utilisé pour découvrir les proxys Web.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
