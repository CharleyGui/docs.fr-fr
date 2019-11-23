---
title: <webRequestModules>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697462"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules >, élément (paramètres réseau)
Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
 Aucune.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|Ajoute un module de demande Web personnalisé à l’application.|  
|[clear](clear-element-for-webrequestmodules-network-settings.md)|Supprime tous les modules de demande Web inscrits de l’application.|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|Supprime un module de demande Web personnalisé de l’application.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Remarques  
 L’élément `webRequestModules` inscrit les descendants de la classe <xref:System.Net.WebRequest> pour gérer les demandes d’informations aux hôtes réseau. Les modules de demande Web doivent implémenter l’interface <xref:System.Net.IWebRequestCreate>.  
  
 Le .NET Framework comprend des modules de demande Web pour les URI qui commencent par `http://`, `https://`et `file://`. Vous pouvez remplacer les modules par défaut uniquement en inscrivant un module personnalisé dans le fichier de configuration.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant enregistre le module HTTP par défaut. Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Schéma des paramètres réseau](index.md)
