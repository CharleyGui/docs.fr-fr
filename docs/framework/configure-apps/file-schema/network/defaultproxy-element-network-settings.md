---
title: <defaultProxy>, élément (paramètres réseau)
description: L' <defaultProxy> élément paramètres réseau configure le serveur proxy http (Hypertext Transfer Protocol) dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 806a30a52219ef9185f84a650d6a8eef8fb0dc8c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190304"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy>, élément (paramètres réseau)

Configure le serveur proxy HTTP (Hypertext Transfer Protocol).  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultProxy  
  enabled="True|False"  
  useDefaultCredentials="True|False">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si un proxy web est utilisé. La valeur par défaut est `True`.|  
|`useDefaultCredentials`|Spécifie si les informations d'identification par défaut associées à cet hôte sont utilisées pour accéder au proxy web. La valeur par défaut est `False`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[BypassList](bypasslist-element-network-settings.md)|Fournit un ensemble d'expressions régulières décrivant les adresses qui n'utilisent pas le proxy.|  
|[modules](module-element-network-settings.md)|Ajoute un nouveau module proxy à l'application.|  
|[procur](proxy-element-network-settings.md)|Définit un serveur proxy.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Notes  

 Si l'élément defaultProxy est vide, les paramètres du proxy Internet Explorer sont utilisés. Ce comportement est différent de la version 1.1 de .NET Framework.  
  
 Une exception est levée si l’élément de [module](module-element-network-settings.md) spécifie un type non public, si le type ne dérive pas de la <xref:System.Net.IWebProxy> classe, une exception du constructeur sans paramètre de cet objet s’est produite, ou une exception s’est produite lors de la récupération du proxy par défaut spécifié par le système. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local et contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
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
- [Schéma des paramètres réseau](index.md)
