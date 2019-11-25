---
title: élément <clear> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088715"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<> élément Clear pour NameValueSectionHandler et DictionarySectionHandler

Efface tous les paramètres précédemment définis dans une section.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la\ >.
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Attributs

aucune.

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ------------|
| [ **\<** de la > Appartient](custom-element-2.md) | Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Éléments enfants

aucune.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’élément **\<clear >** pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l’élément **\<clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de l’ordinateur.

Le code de fichier de configuration d’ordinateur suivant déclare la section **\<> mySection**:

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

Le code de fichier de configuration d’application suivant supprime tous les paramètres de **\<> mySection**. L’application ne peut pas récupérer les paramètres qui ont été déclarés dans le dans la section **\<mySection >** du fichier de configuration de l’ordinateur.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
