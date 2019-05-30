---
title: <sectionGroup>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301195"
---
# <a name="sectiongroup-element-for-configsections"></a>\<sectionGroup >, élément pour \<configSections >

Définit un espace de noms pour les sections de configuration.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**

## <a name="syntax"></a>Syntaxe

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom du groupe de section que vous définissez. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configSections >** élément](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contient des déclarations d’espace de noms et de la section de configuration. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<section>** ](~/docs/framework/configure-apps/file-schema/section-element.md) | Contient une déclaration de section de configuration. |

## <a name="remarks"></a>Notes

Déclaration d’un groupe de section crée une balise de conteneur pour les sections de configuration et permet de s’assurer qu’il n’y a aucun conflit d’affectation de noms avec des sections de configuration définies par quelqu'un d’autre. Vous pouvez imbriquer  **\<sectionGroup >** éléments dans d’autres.

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer un groupe de sections et déclarer des sections dans un groupe de sections :

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
