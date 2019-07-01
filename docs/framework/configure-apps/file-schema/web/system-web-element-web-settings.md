---
title: <system.web>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b9a43c5f5141e364ab9aac1cfdff577a8fb8a161
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486677"
---
# <a name="systemweb-element-web-settings"></a>\<System.Web >, élément (paramètres Web)
Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement au niveau du processus.  
  
 \<configuration>  
\<System.Web >, élément (paramètres Web)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Spécifie les paramètres de configuration pour les pools d’applications IIS dans un fichier aspnet.config.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration qui est utilisé par le common language runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
 Le `system.web` élément et son enfant `applicationPool` élément ont été ajoutées au .NET Framework à partir de .NET Framework 3.5 SP1. Lorsque vous exécutez IIS 7.0 ou versions ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la façon dont ASP.NET gère les threads et comment il les files d’attente les demandes lorsqu’il est hébergé dans un pool d’applications IIS. Si vous exécutez IIS 7.0 ou versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer le comportement au niveau du processus ASP.NET dans le fichier aspnet.config lorsqu’il est hébergé dans un pool d’applications IIS. L’exemple suppose qu’IIS s’exécute dans intégré mode et que l’application utilise le .NET Framework 3.5 SP1 ou une version ultérieure. Ce comportement ne se produit pas dans les versions du .NET Framework antérieures à .NET Framework 3.5 SP1. Les valeurs dans l’exemple sont les valeurs par défaut.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi

- [\<applicationPool >, élément (paramètres Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
