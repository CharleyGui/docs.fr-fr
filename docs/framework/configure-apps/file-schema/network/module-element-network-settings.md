---
title: <module>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154827"
---
# <a name="module-element-network-settings"></a>\<module> Element (Paramètres réseau)
Ajoute un nouveau module proxy à l'application.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<défautProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`type`|Le nom de type entièrement <xref:System.Type.FullName%2A> qualifié (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété) et le nom d’assemblage (indiqué par la propriété), séparés par une virgule, qui implémente le proxy.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Notes   
 L’élément `module` enregistre les classes <xref:System.Net.IWebProxy> proxy qui implémenter l’interface. Après l’enregistrement de `module` la classe de procuration, peut être utilisé pour demander des informations par l’intermédiaire de la procuration prise en charge.  
  
 La valeur `type` de l’attribut doit être le nom de classe du module et le nom de sa bibliothèque dynamique correspondante (DLL).  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant enregistre une classe de proxy personnalisée.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Paramètres réseau Schema](index.md)
