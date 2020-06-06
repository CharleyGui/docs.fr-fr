---
title: <remove>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215497"
---
# <a name="remove-element-for-appsettings"></a>\<remove>, élément de \<appSettings>

Supprime les paramètres d’application personnalisés.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Attribut

|         | Description |
| ------- | ----------- |
| **key** | Attribut requis.<br><br>Spécifie le nom de la clé à supprimer. |

### <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application. |

## <a name="child-elements"></a>Éléments enfants

None

## <a name="example"></a>Exemple

L’exemple suivant montre comment supprimer un paramètre de configuration personnalisé pour `ApplicationName` :

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](../index.md)
