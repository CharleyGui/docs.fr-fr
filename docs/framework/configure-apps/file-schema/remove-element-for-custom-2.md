---
title: <remove>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214757"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<remove>, élément de NameValueSectionHandler et DictionarySectionHandler

Supprime un paramètre défini précédemment.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<add remove="key" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom du paramètre à supprimer. |

## <a name="parent-element"></a>Élément parent

| Élément | Description |
| ------- | ------------|
| [**\<sectionName>** Appartient](custom-element-2.md) | Définit des paramètres pour les sections de configuration personnalisées qui utilisent les <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes et. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes

Vous pouvez utiliser l' **\<remove>** élément pour supprimer de votre application les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l' **\<remove>** élément dans un fichier de configuration de l’application pour supprimer des paramètres précédemment définis dans le fichier de configuration de l’ordinateur.

Le code de fichier de configuration d’ordinateur suivant déclare la section **\<mySection>** et y ajoute deux paramètres `key1` `key2` :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Le code de fichier de configuration de l’application suivant supprime le `key2` paramètre de **\<mySection>** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
