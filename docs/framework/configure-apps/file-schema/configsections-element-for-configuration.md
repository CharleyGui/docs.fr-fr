---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300789"
---
# <a name="configsections-element-for-configuration"></a>\<configSections >, élément pour \<configuration >

Contient des déclarations d’espace de noms et de la section de configuration.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<section>** ](~/docs/framework/configure-apps/file-schema/section-element.md) | Contient une déclaration de section de configuration. |
| [ **\<sectionGroup>** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Définit un espace de noms pour les sections de configuration. |
| [ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Supprime une section prédéfinie ou le groupe de section. |
| [ **\<clear>** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Efface toutes les sections précédemment définies et les groupes de sections. |

## <a name="remarks"></a>Notes

Si cet élément est dans un fichier de configuration, il doit être le premier élément enfant de le  **\<configuration >** élément.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration et de définir les paramètres de cette section :

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

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
