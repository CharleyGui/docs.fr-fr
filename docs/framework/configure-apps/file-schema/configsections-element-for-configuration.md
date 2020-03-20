---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155347"
---
# <a name="configsections-element-for-configuration"></a>\<les> élément de configuration \<>

Contient la section de configuration et les déclarations d’espace nom.

configuration &nbsp; &nbsp;>[** \<**](configuration-element.md) ** \<configSections>**

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<section>**](section-element.md) | Contient une déclaration de section de configuration. |
| [**\<sectionGroupe>**](sectiongroup-element-for-configsections.md) | Définit un espace de nom pour les sections de configuration. |
| [**\<supprimer>**](remove-element-for-configsections.md) | Supprime une section prédéfinie ou un groupe de section. |
| [**\<clair>**](clear-element-for-configsections.md) | Efface toutes les sections et les groupes de section précédemment définis. |

## <a name="remarks"></a>Notes 

Si cet élément est dans un fichier de configuration, ** \<** il doit être le premier élément enfant de la configuration>élément.

## <a name="example"></a> Exemple

L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :

```xml
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

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](index.md)
