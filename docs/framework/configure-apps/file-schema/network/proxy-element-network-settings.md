---
title: <proxy>, élément (paramètres réseau)
description: L' <proxy> élément paramètres réseau définit les options de serveur proxy dans la .NET Framework. Cet article contient un exemple.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141779"
---
# <a name="proxy-element-network-settings"></a>\<proxy>, élément (paramètres réseau)
Définit un serveur proxy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Syntax  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`autoDetect`|Spécifie si le proxy est détecté automatiquement. La valeur par défaut est `Unspecified`.|  
|`bypassonlocal`|Spécifie si le proxy est contourné pour les ressources locales. Les ressources locales incluent le serveur local ( `http://localhost` , `http://loopback` ou `http://127.0.0.1` ) et un URI sans point ( `http://webserver` ). La valeur par défaut est `Unspecified`.|  
|`proxyaddress`|Spécifie l’URI du proxy à utiliser.|  
|`scriptLocation`|Spécifie l’emplacement du script de configuration. N’utilisez pas l' `bypassonlocal` attribut avec cet attribut. |  
|`usesystemdefault`|Spécifie s’il faut utiliser les paramètres de proxy d’Internet Explorer. Si la valeur `True` est, les attributs suivants remplacent les paramètres de proxy d’Internet Explorer. La valeur par défaut est `Unspecified`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Valeur texte  
  
## <a name="remarks"></a>Remarques  
 L' `proxy` élément définit un serveur proxy pour une application. Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilisera les paramètres de proxy dans Internet Explorer.  
  
 La valeur de l' `proxyaddress` attribut doit être un URI (Uniform Resource Indicator) bien formé.  
  
 L' `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration du proxy. La <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé WPAD. dat) lorsque l’option **utiliser le script de configuration automatique** est sélectionnée dans Internet Explorer. Si `bypassonlocal` est défini sur n’importe quelle valeur, `scriptLocation` est ignoré.
  
 Utilisez l' `usesystemdefault` attribut pour les applications .NET Framework version 1,1 qui migrent vers la version 2,0.  
  
 Une exception est levée si l' `proxyaddress` attribut spécifie un proxy par défaut non valide. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
