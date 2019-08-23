---
title: <add>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 594ba4f289012e775e93acba98056b60bdd94cbd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927749"
---
# <a name="add-element-for-appsettings"></a>\<Ajouter > élément pour \<appSettings >

Ajoute un paramètre d’application personnalisé.

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Attributs

|           | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom de la clé à ajouter. |
| **value** | Attribut requis.<br><br>Spécifie la valeur de la clé à ajouter. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter un paramètre de configuration personnalisé pour le nom de l’application:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

L’exemple suivant utilise l' `<add>` élément pour définir deux paramètres de compatibilité dans une application ASP.net:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](../index.md)
