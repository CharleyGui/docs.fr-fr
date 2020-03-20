---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153726"
---
# <a name="section-element"></a>\<section> élément

Contient une déclaration de section de configuration.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<les>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<les>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroupe>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>Syntaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Attributs requis

|           | Description |
| --------- | ----------- |
| **name**  | Spécifie le nom de la section configuration. |
| **type**  | Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section à partir du fichier de configuration. La valeur type a la syntaxe "entièrement qualifié-section-gestionnaire-classe nom, simple-assemblage-nom". Le nom d’assemblage simple est le nom de fichier racine sans l’extension de fichier *.dll.* |

## <a name="optional-attributes"></a>Attributs facultatifs

Les attributs suivants ne s’appliquent qu’aux applications ASP.NET. Le système de configuration ignore ces attributs pour d’autres types d’applications.

|                     | Description |
| ------------------- | ----------- |
| **permettreDefinition** | Précise dans quel fichier de configuration la section peut être utilisée. Utilisez l’une des valeurs suivantes :<br><br>**Partout**<br>Permet d’utiliser la section dans n’importe quel fichier de configuration. Il s’agit de la valeur par défaut.<br>**MachineOnly**<br>Permet à la section d’être utilisée uniquement dans le fichier de configuration de la machine (*Machine.config*).<br>**MachineToApplication**<br>Permet d’utiliser la section dans le fichier de configuration de la machine ou dans le fichier de configuration d’application. |
| **allowLocation**   | Détermine si la section peut être utilisée dans ** \<l’emplacement>** élément. Utilisez l’une des valeurs suivantes :<br><br>**true**<br>Permet d’utiliser la section dans ** \<l’emplacement>** élément. Il s’agit de la valeur par défaut.<br>**false**<br>Ne permet pas que la section soit utilisée dans ** \<l’emplacement>** élément. |

## <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [les>des configections ** \<** Élément](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace nom. |
| [** \<sectionGroupe>** Élément](sectiongroup-element-for-configsections.md) | Définit un espace de nom pour les sections de configuration. |

> [!NOTE]
> Une ** \<section>** élément est un élément enfant des ** \<configSections>** ou ** \<de la sectionGroup>** mais pas les deux.

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes 

La déclaration d’une section de configuration définit essentiellement un nouvel élément pour le fichier de configuration. Le nouvel élément contient des paramètres qu’un gestionnaire de <xref:System.Configuration.IConfigurationSectionHandler> section de configuration (c’est-à-dire une classe qui implémente l’interface) lit. Les attributs et les éléments pour enfants d’une section que vous définissez dépendent du gestionnaire de section que vous utilisez pour lire vos paramètres.

Déclarer un gestionnaire de section de configuration dans le fichier *Machine.config* vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que l’attribut **de définition de permis** ne spécifie le contraire.

## <a name="example"></a> Exemple

L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
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
