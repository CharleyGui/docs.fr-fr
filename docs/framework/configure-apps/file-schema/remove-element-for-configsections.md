---
title: <remove>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4ff9bb537a31e28dbd4b878c1bc04c96262f85ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927458"
---
# <a name="remove-element-for-configsections"></a>\<supprimer > élément pour \<configSections >

Supprime un groupe de sections ou de sections prédéfini.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom de la section ou du groupe de sections à supprimer. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [élément  **>\<configSections**](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace de noms. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

Vous pouvez utiliser l'  **\<élément remove >** pour supprimer de votre application des sections et des groupes de sections qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemples

L’exemple suivant montre comment utiliser l'  **\<élément remove >** dans un fichier de configuration de l’application pour supprimer une section précédemment définie dans le fichier de configuration de l’ordinateur.

Le code de fichier de configuration d’ordinateur suivant déclare la section  **\<sampleSection >** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

Le code de fichier de configuration d’application suivant supprime la  **\<section > sampleSection** . Après la suppression, l’application ne peut pas récupérer les paramètres dans  **\<sampleSection >** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
