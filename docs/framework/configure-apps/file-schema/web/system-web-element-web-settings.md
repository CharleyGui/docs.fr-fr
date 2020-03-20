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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152839"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> Element (Paramètres Web)
Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement à l’échelle du processus.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
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
|[\<applicationPool>](applicationpool-element-web-settings.md)|Spécifie les paramètres de configuration des pools d’applications IIS dans un fichier aspnet.config.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine de chaque fichier de configuration utilisé par les applications ordinaires de l’exécution de la langue et .NET Framework.|  
  
## <a name="remarks"></a>Notes   

L’élément `system.web` et `applicationPool` son élément enfant ont été ajoutés au cadre .NET à partir du cadre .NET 3.5 SP1. Lorsque vous exécutez des versions IIS 7.0 ou ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la façon dont ASP.NET gère les threads et comment il fait la queue des demandes lorsque ASP.NET est hébergé dans un pool d’applications IIS. Si vous exécutez des versions IIS 7.0 ou ultérieures en mode Classic ou ISAPI, ces paramètres sont ignorés.  
  
## <a name="example"></a> Exemple  

L’exemple suivant montre comment configurer ASP.NET comportement à l’échelle du processus dans le fichier aspnet.config lorsque ASP.NET est hébergé dans un pool d’applications IIS. L’exemple suppose que l’IIS est en cours d’exécution en mode intégré et que l’application utilise le cadre .NET 3.5 SP1 ou une version ultérieure. Ce comportement ne se produit pas dans les versions du cadre .NET plus tôt que le cadre .NET 3.5 SP1. Les valeurs dans l’exemple sont les valeurs par défaut.  
  
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

- [\<applicationPool> Element (Paramètres Web)](applicationpool-element-web-settings.md)
