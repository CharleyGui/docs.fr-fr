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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699090"
---
# <a name="systemweb-element-web-settings"></a>@no__t élément -0System. Web > (paramètres Web)
Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement à l’ensemble du processus.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1 **@no__t -3System. web >**  
  
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
|[\<applicationPool>](applicationpool-element-web-settings.md)|Spécifie les paramètres de configuration des pools d’applications IIS dans un fichier Aspnet. config.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.|  
  
## <a name="remarks"></a>Notes  

L’élément `system.web` et son élément enfant `applicationPool` ont été ajoutés à la .NET Framework à partir de .NET Framework 3,5 SP1. Lorsque vous exécutez IIS 7,0 ou des versions ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les threads et la façon dont il met en file d’attente les demandes lorsque ASP.NET est hébergé dans un pool d’applications IIS. Si vous exécutez IIS 7,0 ou des versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
## <a name="example"></a>Exemple  

L’exemple suivant montre comment configurer le comportement à l’ensemble du processus ASP.NET dans le fichier Aspnet. config lorsque ASP.NET est hébergé dans un pool d’applications IIS. L’exemple suppose qu’IIS s’exécute en mode intégré et que l’application utilise le .NET Framework 3,5 SP1 ou une version ultérieure. Ce comportement ne se produit pas dans les versions de la .NET Framework antérieures à la .NET Framework 3,5 SP1. Les valeurs de l’exemple sont les valeurs par défaut.  
  
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

- [\<applicationPool >, élément (paramètres Web)](applicationpool-element-web-settings.md)
