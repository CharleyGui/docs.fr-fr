---
title: Schéma des paramètres d’application
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a67689bd9757f7586881fd910ef6103b1dffeab8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550447"
---
# <a name="app-settings-schema"></a>Schéma des paramètres d’application

Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| Élément | Description |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | Contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application. A un attribut **file** facultatif. |
| [**\<add>**](add-element-for-appsettings.md) | Définit un paramètre. Enfant de **\<appSettings>** . Requiert des attributs **key** et **value**. |
| [**\<clear>**](clear-element-for-appsettings.md) | Efface tous les paramètres. Enfant de **\<appSettings>** . N’a pas d’attributs. |
| [**\<remove>**](remove-element-for-appsettings.md) | Supprime un paramètre. Enfant de **\<appSettings>** . Exige un attribut **key**. |

## <a name="appsettings-element"></a>\<appSettings>, élément

Cet élément contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application. Il définit un attribut facultatif pour **file**.

## <a name="add-element"></a>\<add>, élément

Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application. Il définit les attributs pour **key** et **value**.

## <a name="clear-element"></a>\<clear>, élément

Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références qui sont ajoutées par **\<add>** les éléments qui suivent l' **\<clear>** élément. Il ne définit aucun attribut.

## <a name="remove-element"></a>\<remove>, élément

Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application. Il définit un attribut pour **key**.

## <a name="example"></a> Exemple

L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des paramètres d'application](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [Architecture des paramètres d'application](/dotnet/desktop/winforms/advanced/application-settings-architecture)
