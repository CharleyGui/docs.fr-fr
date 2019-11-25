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
ms.openlocfilehash: 5f327a2bb4fe316497614f14669907d514c20654
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089193"
---
# <a name="proxy-element-network-settings"></a>Élément \<proxy > (paramètres réseau)
Définit un serveur proxy.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy**](defaultproxy-element-network-settings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >

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
|`bypassonlocal`|Spécifie si le proxy est contourné pour les ressources locales. Les ressources locales incluent le serveur local (`http://localhost`, `http://loopback`ou `http://127.0.0.1`) et un URI sans point (`http://webserver`). La valeur par défaut est `unspecified`.|  
|`proxyaddress`|Spécifie l’URI du proxy à utiliser.|  
|`scriptLocation`|Spécifie l’emplacement du script de configuration. N’utilisez pas l’attribut `bypassonlocal` avec cet attribut. |  
|`usesystemdefault`|Spécifie s’il faut utiliser les paramètres de proxy d’Internet Explorer. Si la valeur est `true`, les attributs suivants remplacent les paramètres de proxy d’Internet Explorer. La valeur par défaut est `unspecified`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Valeur texte  
  
## <a name="remarks"></a>Notes  
 L’élément `proxy` définit un serveur proxy pour une application. Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilisera les paramètres de proxy dans Internet Explorer.  
  
 La valeur de l’attribut `proxyaddress` doit être un URI (Uniform Resource Indicator) bien formé.  
  
 L’attribut `scriptLocation` fait référence à la détection automatique des scripts de configuration du proxy. La classe <xref:System.Net.WebProxy> tente de localiser un script de configuration (généralement nommé WPAD. dat) lorsque l’option **utiliser le script de configuration automatique** est sélectionnée dans Internet Explorer. Si `bypassonlocal` est définie sur une valeur quelconque, `scriptLocation` est ignoré.
  
 Utilisez l’attribut `usesystemdefault` pour les applications .NET Framework version 1,1 qui migrent vers la version 2,0.  
  
 Une exception est levée si l’attribut `proxyaddress` spécifie un proxy par défaut non valide. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.  
  
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
- [Schéma des paramètres réseau](index.md)
