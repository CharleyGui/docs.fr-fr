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
ms.openlocfilehash: 64556054df2689ff758f52c7e98556997a3e9d3d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301183"
---
# <a name="section-element"></a>\<section > élément

Contient une déclaration de section de configuration.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup>** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
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
| **type**  | Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section du fichier de configuration. La valeur de type a la syntaxe « fully-qualified-section-handler-class-name, nom de l’assembly simple ». Le nom d’assembly simple est le nom de fichier racine sans le *.dll* extension de fichier. |

## <a name="optional-attributes"></a>Attributs facultatifs

Les attributs suivants sont applicables uniquement pour les applications ASP.NET. Le système de configuration ignore ces attributs pour les autres types d’application.

|                     | Description |
| ------------------- | ----------- |
| **allowDefinition** | Spécifie la section peut être utilisée dans le fichier de configuration. Utilisez l'une des valeurs suivantes :<br><br>**Partout**<br>Permet à la section peut être utilisée dans n’importe quel fichier de configuration. Il s'agit de la valeur par défaut.<br>**MachineOnly**<br>La section peut être utilisé uniquement dans le fichier de configuration de machine (*Machine.config*).<br>**MachineToApplication**<br>Permet à la section peut être utilisée dans le fichier de configuration machine ou le fichier de configuration d’application. |
| **allowLocation**   | Détermine si la section peut être utilisée dans le  **\<emplacement >** élément. Utilisez l'une des valeurs suivantes :<br><br>**true**<br>Permet à la section au sein de la  **\<emplacement >** élément. Il s'agit de la valeur par défaut.<br>**false**<br>N’autorise pas la section au sein de la  **\<emplacement >** élément. |

## <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [ **\<configSections >** élément](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contient des déclarations d’espace de noms et de la section de configuration. |
| [ **\<sectionGroup >** élément](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Définit un espace de noms pour les sections de configuration. |

> [!NOTE]
> Un  **\<section >** élément est un élément enfant du  **\<configSections >** ou  **\<sectionGroup >** mais pas les deux.

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes

Déclaration essentiellement d’une section de configuration définit un nouvel élément pour le fichier de configuration. Le nouvel élément contient une configuration de gestionnaire de section de paramètres (autrement dit, une classe qui implémente le <xref:System.Configuration.IConfigurationSectionHandler> interface) lit. Les attributs et les éléments enfants d’une section, que vous définissez varient selon le Gestionnaire de section que vous utilisez pour lire vos paramètres.

Déclaration d’un gestionnaire de section de configuration dans le *Machine.config* fichier vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, sauf si le **allowDefinition**attribut spécifie autrement.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration et de définir les paramètres de cette section :

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

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
