---
title: <add>, élément de bypasslist (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155075"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<ajouter> Element pour la bypasslist (Paramètres réseau)
Ajoute une adresse IP ou un nom DNS à la liste de contournement par procuration.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de la liste de contournement**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|**Adresse**|Une expression régulière décrivant une adresse IP ou un nom DNS.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas un proxy.|  
  
## <a name="remarks"></a>Notes   
 L’élément `add` insère des expressions régulières décrivant les adresses IP ou les noms de serveur DNS à la liste des adresses qui contournent un serveur proxy.  
  
 La valeur `address` de l’attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôte.  
  
 Vous devez faire preuve de prudence lorsque vous spécifiez une expression régulière pour cet élément. L’expression régulière "[a-z]md\\\\.contoso .com" correspond à n’importe quel hôte dans le domaine contoso.com, mais elle correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com. Pour n’égaler qu’un hôte dans le domaine contoso.com, utilisez une ancre\\(«$») : « [a-z]md .contoso\\.com$.  
  
 Pour plus d’informations sur les expressions régulières, voir . [.NET Framework Expressions régulières](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant ajoute deux adresses à la liste de contournement. Le premier contourne le proxy pour tous les serveurs du domaine contoso.com ; le second contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192.168.  
  
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
