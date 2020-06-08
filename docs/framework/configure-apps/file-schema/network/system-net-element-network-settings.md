---
title: <system.Net>, élément (paramètres réseau)
description: L’élément paramètres réseau <system.Net> contient des paramètres qui spécifient la façon dont le .NET Framework se connecte aux options réseau dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504483"
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
  
|**Appartient**|**Description**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les requêtes Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à un hôte Internet.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).|  
|[requestCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour les classes dans les <xref:System.Net> espaces de noms enfants associés.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à partir d’hôtes Internet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Appartient**|**Description**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|Contient les paramètres de tous les espaces de noms.|  
  
## <a name="remarks"></a>Remarques  
 L' [\<system.net>](system-net-element-network-settings.md) élément contient des paramètres pour les classes dans les <xref:System.Net> espaces de noms enfants associés. Les paramètres configurent les modules d’authentification, la gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demande Internet pour la réception d’informations à partir d’hôtes Internet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une configuration classique utilisée par les <xref:System.Net> classes.  
  
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
