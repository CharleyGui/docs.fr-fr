---
title: <remove>, élément de bypasslist (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697892"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<supprimer > élément de bypasslist (paramètres réseau)

Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.

[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy** >](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BypassList >** ](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**supprimer >**  

## <a name="syntax"></a>Syntaxe

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributes

|**Attribut**|**Description**|
|-------------------|---------------------|
|`address`|Expression régulière décrivant une adresse IP ou un nom DNS.|

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|-----------------|---------------------|
|[bypasslist](bypasslist-element-network-settings.md)|Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.|

## <a name="remarks"></a>Remarques

L’élément `remove` supprime les expressions régulières décrivant des adresses IP ou des noms de serveurs DNS de la liste des adresses qui contournent un serveur proxy. Les adresses ont été définies précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.

La valeur de l’attribut `address` doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôte.

Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Fichiers de configuration

Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).

## <a name="example"></a>Exemple

L’exemple suivant supprime toute définition précédente du domaine adventure-works.com, puis ajoute le domaine contoso.com à la liste de contournement.

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
