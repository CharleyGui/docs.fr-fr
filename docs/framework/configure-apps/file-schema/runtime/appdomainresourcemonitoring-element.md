---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154374"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring> Element
Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Précise si le temps d’exécution recueille des statistiques pour la surveillance des ressources de domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Les statistiques relatives à la surveillance des ressources du domaine des applications sont recueillies.|  
|`false`|Les statistiques relatives à la surveillance des ressources du domaine des applications ne sont pas recueillies.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 La surveillance des ressources de domaine d’application est disponible via la classe de domaine d’application gérée, l’interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) et le traçage d’événements pour Windows (ETW). Lorsque la surveillance est activée, des statistiques sont collectées pour tous les domaines d’application dans le processus pour la durée du processus.  
  
 Pour permettre la surveillance à <xref:System.AppDomain.MonitoringIsEnabled%2A> partir du code géré, utilisez la propriété.  
  
 Cet élément de configuration n’est disponible que dans le cadre .NET 4 et plus tard.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment activer la surveillance des ressources de domaine d’application.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
