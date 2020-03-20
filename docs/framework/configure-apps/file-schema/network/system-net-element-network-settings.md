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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154554"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net>, élément (paramètres réseau)
Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les demandes Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Spécifie le nombre maximum de connexions à un hébergeur Internet.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
|[mailSettings (en)](mailsettings-element-network-settings.md)|Configure les options d’envoi de courrier simple par protocole de transport de courrier (SMTP).|  
|[demandeCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache des demandes de réseau.|  
|[source de données](settings-element-network-settings.md)|Configure les options réseau de <xref:System.Net> base pour les classes dans les espaces nominaux pour enfants et les enfants apparentés.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations aux hébergeurs Internet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|Contient des paramètres pour tous les espaces de noms.|  
  
## <a name="remarks"></a>Notes   
 [ \<L’élément system.net>](system-net-element-network-settings.md) contient des paramètres pour <xref:System.Net> les classes dans les espaces nominaux des enfants et connexes. Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour recevoir des informations provenant d’hébergeurs Internet.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre une <xref:System.Net> configuration typique utilisée par les classes.  
  
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

- [Paramètres réseau Schema](index.md)
