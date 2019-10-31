---
title: Schéma des paramètres d’application
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b931b76aa09b3f62fbd799990975268af4f7293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119220"
---
# <a name="app-settings-schema"></a>Schéma des paramètres d’application

Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](remove-element-for-appsettings.md)

| Élément | Description |
| ------- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Contient des balises **\<add>** , **\<clear>** et **\<remove>** pour contrôler les paramètres d’application. A un attribut **file** facultatif. |
| [ **\<add>** ](add-element-for-appsettings.md) | Définit un paramètre. Enfant de **\<appSettings>** . Requiert des attributs **key** et **value**. |
| [ **\<clear>** ](clear-element-for-appsettings.md) | Efface tous les paramètres. Enfant de **\<appSettings>** . N’a pas d’attributs. |
| [ **\<remove>** ](remove-element-for-appsettings.md) | Supprime un paramètre. Enfant de **\<appSettings>** . Exige un attribut **key**. |

## <a name="appsettings-element"></a>\<appSettings>, élément

Cet élément contient des balises **\<add>** , **\<clear>** et **\<remove>** pour contrôler les paramètres d’application. Il définit un attribut facultatif pour **file**.

## <a name="add-element"></a>\<add>, élément

Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application. Il définit les attributs pour **key** et **value**.

## <a name="clear-element"></a>\<clear>, élément

Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références ajoutées par les éléments **\<add>** suivant l’élément **\<clear>** . Il ne définit aucun attribut.

## <a name="remove-element"></a>\<remove>, élément

Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application. Il définit un attribut pour **key**.

## <a name="example"></a>Exemple

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

- [Vue d'ensemble des paramètres d'application](../../../winforms/advanced/application-settings-overview.md)
- [Architecture des paramètres d'application](../../../winforms/advanced/application-settings-architecture.md)
