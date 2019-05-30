---
title: <clear>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301297"
---
# <a name="clear-element-for-appsettings"></a>\<Désactivez >, élément pour \<appSettings >

Efface les paramètres d’application personnalisés.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Attributs

None

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Contient les paramètres d’application personnalisés, tels que les chemins d’accès, des URL de service Web XML ou d’autres informations de configuration d’application personnalisée. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="example"></a>Exemple

L’exemple suivant montre comment effacer les paramètres de configuration personnalisée :

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
