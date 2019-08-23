---
title: <section> d'élément
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 94f7709f4bd273515d9fcdd727354ec579c46207
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927225"
---
# <a name="section-element"></a>\<section > élément

Contient une déclaration de section de configuration.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**

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
| **name**  | Spécifie le nom de la section de configuration. |
| **type**  | Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section dans le fichier de configuration. La valeur de type a la syntaxe «Complete-Class-Handler-Class-Name, simple-assembly-name». Le nom d’assembly simple est le nom de fichier racine sans l’extension de fichier *. dll* . |

## <a name="optional-attributes"></a>Attributs facultatifs

Les attributs suivants s’appliquent uniquement aux applications ASP.NET. Le système de configuration ignore ces attributs pour d’autres types d’applications.

|                     | Description |
| ------------------- | ----------- |
| **allowDefinition** | Spécifie le fichier de configuration dans lequel la section peut être utilisée. Utilisez l’une des valeurs suivantes :<br><br>**Importe**<br>Autorise l’utilisation de la section dans n’importe quel fichier de configuration. Il s'agit de la valeur par défaut.<br>**MachineOnly**<br>Autorise uniquement l’utilisation de la section dans le fichier de configuration de l’ordinateur (*machine. config*).<br>**MachineToApplication**<br>Autorise l’utilisation de la section dans le fichier de configuration de l’ordinateur ou dans le fichier de configuration de l’application. |
| **allowLocation**   | Détermine si la section peut être utilisée dans l'  **\<emplacement >** élément. Utilisez l’une des valeurs suivantes :<br><br>**true**<br>Autorise l’utilisation de la section dans l'  **\<emplacement >** élément. Il s'agit de la valeur par défaut.<br>**false**<br>N’autorise pas l’utilisation de la section dans l'  **\<emplacement >** élément. |

## <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [élément  **>\<configSections**](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace de noms. |
| [sectionGroup >, élément  **\<** ](sectiongroup-element-for-configsections.md) | Définit un espace de noms pour les sections de configuration. |

> [!NOTE]
> **Une\<section >** élément est un élément enfant de  **\<configSections >** ou  **\<de sectionGroup >** , mais pas les deux.

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

La déclaration d’une section de configuration définit essentiellement un nouvel élément pour le fichier de configuration. Le nouvel élément contient les paramètres qu’un gestionnaire de section de configuration (autrement dit, une classe qui <xref:System.Configuration.IConfigurationSectionHandler> implémente l’interface) lit. Les attributs et les éléments enfants d’une section que vous définissez dépendent du gestionnaire de section que vous utilisez pour lire vos paramètres.

La déclaration d’un gestionnaire de section de configuration dans le fichier *machine. config* vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que l’attribut **allowDefinition** spécifie autrement.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section:

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

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
