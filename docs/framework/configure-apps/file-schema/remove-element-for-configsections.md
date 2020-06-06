---
title: <remove>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154528"
---
# <a name="remove-element-for-configsections"></a>\<remove>, élément de \<configSections>

Supprime un groupe de sections ou de sections prédéfini.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

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
| [**\<configSections>** Appartient](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace de noms. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes

Vous pouvez utiliser l' **\<remove>** élément pour supprimer de votre application des sections et des groupes de sections qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l' **\<remove>** élément dans un fichier de configuration de l’application pour supprimer une section précédemment définie dans le fichier de configuration de l’ordinateur.

Le code de fichier de configuration d’ordinateur suivant déclare la section **\<sampleSection>** :

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

Le code de fichier de configuration de l’application suivant supprime la **\<sampleSection>** section. Après la suppression, l’application ne peut pas récupérer les paramètres dans **\<sampleSection>** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
