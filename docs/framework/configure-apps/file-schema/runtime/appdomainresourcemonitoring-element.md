---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad0ae023215eeb1f42f9351369ee77d41d537b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487732"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring > élément
Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.  
  
 \<configuration>  
\<runtime>  
\<appDomainResourceMonitoring>  
  
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
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime collecte des statistiques pour l’analyse de ressource de domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`true`|Statistiques pour l’analyse de ressource de domaine d’application sont collectées.|  
|`false`|Statistiques pour l’analyse de ressource de domaine d’application ne sont pas collectées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 L’analyse de ressource de domaine d’application est disponible via la classe de domaine d’application managée, l’hébergement [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface et le suivi d’événements pour Windows (ETW). Lorsque l’analyse est activée, les statistiques sont collectées pour tous les domaines d’application dans le processus pour la durée de vie du processus.  
  
 Pour activer l’analyse du code managé, utilisez le <xref:System.AppDomain.MonitoringIsEnabled%2A> propriété.  
  
 Cet élément de configuration est disponible uniquement dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer l’analyse de ressource de domaine d’application.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
