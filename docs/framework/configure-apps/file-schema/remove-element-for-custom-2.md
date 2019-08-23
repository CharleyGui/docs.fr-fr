---
title: <remove>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920946"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<supprimer > élément pour NameValueSectionHandler et DictionarySectionHandler

Supprime un paramètre défini précédemment.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

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
| [élément de >y  **\<** ](custom-element-2.md) | Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

Vous pouvez utiliser l'  **\<élément remove >** pour supprimer de votre application les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemples

L’exemple suivant montre comment utiliser l'  **\<élément remove >** dans un fichier de configuration de l’application pour supprimer des paramètres précédemment définis dans le fichier de configuration de l’ordinateur.

Le code de fichier de configuration de l’ordinateur suivant déclare la section  **\<mySection >** et y `key1` ajoute `key2`deux paramètres:

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

Le code de fichier de configuration de l' `key2` application suivant supprime le paramètre de  **\<mySection >** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
