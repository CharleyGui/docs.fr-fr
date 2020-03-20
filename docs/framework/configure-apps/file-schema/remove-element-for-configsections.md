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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154528"
---
# <a name="remove-element-for-configsections"></a>\<supprimer> élément \<pour les> de configSections

Supprime une section prédéfinie ou un groupe de section.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<les>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<supprimer>**

## <a name="syntax"></a>Syntaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom de la section ou du groupe de section à supprimer. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [les>des configections ** \<** Élément](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace nom. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes 

Vous pouvez ** \<** utiliser l’élément de suppression>pour supprimer les sections et les groupes de section de votre application qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser ** \<l’élément de suppression>** dans un fichier de configuration d’application pour supprimer une section précédemment définie dans le fichier de configuration de la machine.

Le code de fichier de configuration de la machine suivante déclare l’échantillon de ** \<sectionSection>**:

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

Le code de fichier de ** \<** configuration d’application suivant supprime la section de>échantillons. Après la suppression, l’application ne peut pas récupérer les paramètres dans ** \<sampleSection>**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](index.md)
