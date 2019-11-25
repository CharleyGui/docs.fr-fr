---
title: <clear>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088734"
---
# <a name="clear-element-for-appsettings"></a>\<> élément Clear pour \<appSettings >

Efface les paramètres d’application personnalisés.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Attributs

aucune.

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Contient des paramètres d’application personnalisés, tels que des chemins d’accès aux fichiers, des URL de service Web XML ou d’autres informations de configuration d’application personnalisées. |

## <a name="child-elements"></a>Éléments enfants

aucune.

## <a name="example"></a>Exemple

L’exemple suivant montre comment effacer les paramètres de configuration personnalisés :

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](../index.md)
