---
title: <clear>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927712"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Clear >, élément de NameValueSectionHandler et DictionarySectionHandler

Efface tous les paramètres précédemment définis dans une section.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Attributs

Aucun

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ------------|
| [élément de >y  **\<** ](custom-element-2.md) | Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

Vous pouvez utiliser l'  **\<élément clear >** pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l'  **\<élément clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans la configuration de l’ordinateur. txt.

Le code de fichier de configuration d’ordinateur suivant déclare la section  **\<mySection >** :

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

Le code de fichier de configuration d’application suivant supprime tous les paramètres de  **\<mySection >** . L’application ne peut pas récupérer les paramètres qui ont été déclarés dans la  **\<section de > mySection** du fichier de configuration de l’ordinateur.

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
