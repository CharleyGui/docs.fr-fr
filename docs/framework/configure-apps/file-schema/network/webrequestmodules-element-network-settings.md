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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154541"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules>, élément (paramètres réseau)
Spécifie les modules à utiliser pour demander des informations aux hôtes du réseau.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](add-element-for-webrequestmodules-network-settings.md)|Ajoute un module de demande Web personnalisé à l’application.|  
|[Clair](clear-element-for-webrequestmodules-network-settings.md)|Supprime tous les modules de demande Web enregistrés de l’application.|  
|[retirer](remove-element-for-webrequestmodules-network-settings.md)|Supprime un module de demande Web personnalisé de l’application.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Notes   
 L’élément `webRequestModules` enregistre les <xref:System.Net.WebRequest> descendants de la classe pour traiter les demandes d’information aux hôtes réseau. Les modules de <xref:System.Net.IWebRequestCreate> demande Web doivent implémenter l’interface.  
  
 Le cadre .NET comprend des modules de `http://`demande `https://`Web `file://`pour les URI qui commencent par , , et . Vous ne pouvez remplacer les modules par défaut qu’en enregistrant un module personnalisé dans le fichier de configuration.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant enregistre le module HTTP par défaut. Vous devez remplacer les valeurs de Version et PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
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
- [Paramètres réseau Schema](index.md)
