---
title: <system.Net>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697502"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net>, élément (paramètres réseau)
Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. net >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
 Aucune.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les requêtes Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à un hôte Internet.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).|  
|[requestCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour les classes du <xref:System.Net> et les espaces de noms enfants associés.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à partir d’hôtes Internet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|Contient les paramètres de tous les espaces de noms.|  
  
## <a name="remarks"></a>Remarques  
 L’élément [\<System. net >](system-net-element-network-settings.md) contient des paramètres pour les classes du <xref:System.Net> et des espaces de noms enfants associés. Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour la réception d’informations à partir d’hôtes Internet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une configuration classique utilisée par les classes <xref:System.Net>.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres réseau](index.md)
