---
title: <bypasslist>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154944"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> Element (Paramètres réseau)
Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas un proxy.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de la liste de contournement**

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
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](add-element-for-bypasslist-network-settings.md)|Ajoute une adresse IP ou un nom DNS à la liste de contournement par procuration.|  
|[Clair](clear-element-for-bypasslist-network-settings.md)|Efface la liste de contournement.|  
|[retirer](remove-element-for-bypasslist-network-settings.md)|Supprime une adresse IP ou un nom DNS de la liste de contournement par procuration.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Notes   
 La liste de contournement contient <xref:System.Net.WebRequest> des expressions régulières qui décrivent les URL qui s’ent entrent directement au lieu de via le serveur proxy.  
  
 Vous devez faire preuve de prudence lorsque vous spécifiez une expression régulière pour cet élément. L’expression régulière "[a-z]md\\\\.contoso .com" correspond à n’importe quel hôte dans le domaine contoso.com, mais elle correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com. Pour n’égaler qu’un hôte dans le domaine contoso.com, utilisez une ancre\\(«$») : « [a-z]md .contoso\\.com$.  
  
 Pour plus d’informations sur les expressions régulières, voir . [.NET Framework Expressions régulières](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant ajoute deux adresses à la liste de contournement. Le premier contourne le proxy pour tous les serveurs du domaine contoso.com ; le second contourne le proxy pour tous les serveurs dont les adresses IP commencent par 192.168.  
  
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
- [Paramètres réseau Schema](index.md)
