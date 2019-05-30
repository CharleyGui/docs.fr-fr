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
ms.openlocfilehash: 7c0173879c692588cc2e15f0b14a5687bb0404fb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300673"
---
# <a name="remove-element-for-configsections"></a>\<Supprimer >, élément pour \<configSections >

Supprime une section prédéfinie ou le groupe de section.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom de la section ou le groupe de section à supprimer. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configSections >** élément](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contient des déclarations d’espace de noms et de la section de configuration. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="remarks"></a>Notes

Vous pouvez utiliser la  **\<Supprimer >** élément à supprimer des sections et groupes de votre application qui ont été définies à un niveau supérieur dans la hiérarchie de fichiers de configuration.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le  **\<Supprimer >** élément dans un fichier de configuration d’application pour supprimer une section précédemment définie dans le fichier de configuration machine.

Le code du fichier de configuration machine suivant déclare la section  **\<sampleSection >** :

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

Le code suivant du fichier de configuration de l’application supprime le  **\<sampleSection >** section. Après la suppression, l’application ne peut pas récupérer les paramètres dans  **\<sampleSection >** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
