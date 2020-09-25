---
title: <bypasslist>, élément (paramètres réseau)
description: L' <bypasslist> élément paramètres réseau fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178409"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist>, élément (paramètres réseau)

Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.|  
|[clear](clear-element-for-bypasslist-network-settings.md)|Efface la liste de contournement.|  
|[remove](remove-element-for-bypasslist-network-settings.md)|Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Notes  

 La liste de contournement contient des expressions régulières qui décrivent les URI qui <xref:System.Net.WebRequest> excèdent directement l’accès au serveur proxy.  
  
 Vous devez faire attention lorsque vous spécifiez une expression régulière pour cet élément. L’expression régulière "[a-z] + \\ . contoso \\ . com" correspond à n’importe quel hôte dans le domaine contoso.com, mais correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com. Pour correspondre uniquement à un hôte dans le domaine contoso.com, utilisez un point d’ancrage (« $ ») : « [a-z] + \\ . contoso \\ . com $ ».  
  
 Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant ajoute deux adresses à la liste de contournement. La première contourne le proxy pour tous les serveurs dans le domaine contoso.com. la deuxième contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192,168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
