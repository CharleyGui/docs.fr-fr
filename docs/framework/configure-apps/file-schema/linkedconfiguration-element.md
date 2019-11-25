---
title: <linkedConfiguration> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087962"
---
# <a name="linkedconfiguration-element"></a>\<élément linkedConfiguration >

Spécifie un fichier de configuration à inclure.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration** >

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **href**  | Attribut requis.<br><br>URL du fichier de configuration à inclure. Le seul format pris en charge pour l’attribut **href** est `file://`. Les fichiers locaux et les fichiers UNC sont pris en charge. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<assemblyBinding >** Appartient](assemblybinding-element-for-configuration.md) | Spécifie la stratégie de liaison de l’assembly au niveau de la configuration. |

## <a name="child-elements"></a>Éléments enfants

aucune.

## <a name="remarks"></a>Notes

L’élément **\<linkedConfiguration >** simplifie la maintenance des assemblys de composants. Si une ou plusieurs applications utilisent un assembly qui a un fichier de configuration résidant dans un emplacement connu, les fichiers de configuration des applications qui utilisent l’assembly peuvent utiliser l’élément **\<linkedConfiguration >** pour inclure le fichier de configuration de l’assembly, plutôt que d’inclure directement les informations de configuration. Lorsque l’assembly de composant est desservi, la mise à jour du fichier de configuration commun fournit des informations de configuration mises à jour à toutes les applications qui utilisent l’assembly.

> [!NOTE]
> L’élément **\<linkedConfiguration >** n’est pas pris en charge pour les applications avec des manifestes côte à côte Windows.

Les règles suivantes régissent l’utilisation des fichiers de configuration liés :

- Les paramètres dans les fichiers de configuration inclus affectent uniquement la stratégie de liaison du chargeur et sont utilisés uniquement par le chargeur. Les fichiers de configuration inclus peuvent avoir des paramètres autres que des stratégies de liaison, mais ces paramètres n’ont aucun effet.

- Le seul format pris en charge pour l’attribut `href` est `file://`. Les fichiers locaux et les fichiers UNC sont pris en charge.

- Il n’existe aucune contrainte sur le nombre de configurations liées par fichier de configuration.

- Tous les fichiers de configuration liés sont fusionnés pour former un fichier, de la même façon que le comportement de laC++directive `#include` en C/.

- L’élément **\<linkedConfiguration >** est autorisé uniquement dans les fichiers de configuration de l’application ; elle est ignorée dans le *fichier machine. config*.

- Les références circulaires sont détectées et arrêtées. Autrement dit, si le **\<linkedConfiguration >** éléments d’une série de fichiers de configuration forment une boucle, la boucle est détectée et arrêtée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment inclure le fichier de configuration à partir du disque dur local :

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [ **\<assemblyBinding >** Appartient](assemblybinding-element-for-configuration.md)
- [Schéma du fichier de configuration pour le .NET Framework](index.md)
