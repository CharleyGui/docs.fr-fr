---
title: <defaultProxy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 5947808cd137fc4cd280ac683a3e9a14b0d4644d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363862"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy >, élément (paramètres réseau)
Configure le serveur proxy HTTP (Hypertext Transfer Protocol).  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si un proxy web est utilisé. La valeur par défaut est `true`.|  
|`useDefaultCredentials`|Spécifie si les informations d'identification par défaut associées à cet hôte sont utilisées pour accéder au proxy web. La valeur par défaut est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fournit un ensemble d'expressions régulières décrivant les adresses qui n'utilisent pas le proxy.|  
|[module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Ajoute un nouveau module proxy à l'application.|  
|[proxy](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Définit un serveur proxy.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Notes  
 Si l'élément defaultProxy est vide, les paramètres du proxy Internet Explorer sont utilisés. Ce comportement est différent de la version 1.1 de .NET Framework.  
  
 Une exception est levée si l’élément de [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) spécifie un type non public, si le type ne dérive pas <xref:System.Net.IWebProxy> de la classe, une exception du constructeur sans paramètre de cet objet s’est produite, ou une exception s’est produite lors de la récupération du proxy par défaut spécifié par le système. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local et contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
