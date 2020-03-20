---
title: <proxy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154788"
---
# <a name="proxy-element-network-settings"></a>\<élément> proxy (Paramètres réseau)
Définit un serveur proxy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>par procuration**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`autoDetect`|Spécifie si le proxy est détecté automatiquement. La valeur par défaut est `unspecified`.|  
|`bypassonlocal`|Spécifie si le proxy est contourné pour les ressources locales. Les ressources locales`http://localhost`comprennent `http://loopback`le `http://127.0.0.1`serveur local ( ,`http://webserver`, ou ) et un URI sans période ( ). La valeur par défaut est `unspecified`.|  
|`proxyaddress`|Spécifie l’URI proxy à utiliser.|  
|`scriptLocation`|Spécifie l’emplacement du script de configuration. N’utilisez `bypassonlocal` pas l’attribut avec cet attribut. |  
|`usesystemdefault`|Précise s’il faut utiliser les paramètres de proxy Internet Explorer. Si défini `true`à , attributs ultérieurs remplacera les paramètres de proxy Internet Explorer. La valeur par défaut est `unspecified`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Valeur texte  
  
## <a name="remarks"></a>Notes   
 L’élément `proxy` définit un serveur proxy pour une application. Si cet élément est absent du fichier de configuration, alors le cadre .NET utilisera les paramètres proxy dans Internet Explorer.  
  
 La valeur `proxyaddress` de l’attribut devrait être un indicateur uniforme bien formé des ressources (URI).  
  
 L’attribut `scriptLocation` se réfère à la détection automatique des scripts de configuration proxy. La <xref:System.Net.WebProxy> classe tentera de localiser un script de configuration (généralement appelé Wpad.dat) lorsque **l’option de script de configuration automatique Utiliser** est sélectionnée dans Internet Explorer. Si `bypassonlocal` est réglé à `scriptLocation` une valeur quelconque, est ignoré.
  
 Utilisez `usesystemdefault` l’attribut pour les applications .NET Framework version 1.1 qui migrent vers la version 2.0.  
  
 Une exception est `proxyaddress` lancée si l’attribut spécifie un proxy par défaut invalide. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant utilise les défauts du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Paramètres réseau Schema](index.md)
