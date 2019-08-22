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
ms.openlocfilehash: 0fd8de9af00aa861d92c8c201ef89545e108c790
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659239"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<supprimer > élément pour BypassList (paramètres réseau)

Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.

\<configuration>\
\<system.net>\
\<defaultProxy>\
\<BypassList > \
\<remove>

## <a name="syntax"></a>Syntaxe

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|**Attribut**|**Description**|
|-------------------|---------------------|
|`address`|Expression régulière décrivant une adresse IP ou un nom DNS.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|-----------------|---------------------|
|[bypasslist](bypasslist-element-network-settings.md)|Fournit un ensemble d’expressions régulières qui décrivent les adresses qui n’utilisent pas de proxy.|

## <a name="remarks"></a>Notes

L' `remove` élément supprime les expressions régulières décrivant des adresses IP ou des noms de serveurs DNS de la liste des adresses qui contournent un serveur proxy. Les adresses ont été définies précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.

La valeur de l' `address` attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou de noms d’hôtes.

Pour plus d’informations sur les expressions régulières, consultez. [.NET Framework des expressions régulières](../../../../../docs/standard/base-types/regular-expressions.md).

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
