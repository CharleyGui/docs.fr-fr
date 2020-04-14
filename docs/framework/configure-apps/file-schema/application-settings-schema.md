---
title: Schéma paramètres d’application
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242827"
---
# <a name="application-settings-schema"></a>Schéma paramètres d’application

Les paramètres d’application permettent à un formulaire Windows ou à une application ASP.NET de stocker et de récupérer les paramètres d’application et d’utilisation. Dans ce contexte, un *paramètre* est toute information spécifique à l’application ou spécifique à l’utilisateur actuel — n’importe quoi d’une chaîne de connexion de base de données à la taille de fenêtre par défaut préférée de l’utilisateur.

Par défaut, les paramètres d’application <xref:System.Configuration.LocalFileSettingsProvider> d’une application Windows Forms utilisent la classe, qui utilise le système de configuration .NET pour stocker les paramètres d’un fichier de configuration XML. Pour plus d’informations sur les fichiers utilisés par les paramètres d’application, voir [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).

Les paramètres d’application définissent les éléments suivants dans les fichiers de configuration qu’il utilise.

| Élément                    | Description                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | Contient tous les ** \<réglages>** des balises spécifiques à l’application.                         |
| **\<userSettings>**        | Contient tous les ** \<réglages>** des balises spécifiques à l’utilisateur actuel.                        |
| **\<>de réglage**             | Définit un paramètre. Enfant ** \<d’applicationsSettings>** ou ** \<userSettings>**. |
| **\<>de valeur**               | Définit la valeur d’un paramètre. Enfant ** \< **de réglage>.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> élément

Cet élément contient tous les ** \<réglages>** balises qui sont spécifiques à une instance de l’application sur un ordinateur client. Il ne définit aucun attribut.

## <a name="usersettings-element"></a>\<userSettings> élément

Cet élément contient tous les ** \<réglages>** balises qui sont spécifiques à l’utilisateur qui utilise actuellement l’application. Il ne définit aucun attribut.

## <a name="setting-element"></a>\<réglage> élément

Cet élément définit un paramètre. Il a les attributs suivants.

| Attribut        | Description |
| ---------------- | ----------- |
| **name**         | Obligatoire. L’ID unique du réglage. Les paramètres créés par Visual `ProjectName.Properties.Settings`Studio sont enregistrés avec le nom . |
| **serializeAs** | Obligatoire. Le format à utiliser pour sérialiser la valeur du texte. Les valeurs autorisées sont :<br><br>- `string`. La valeur est sérialisée <xref:System.ComponentModel.TypeConverter>comme une chaîne en utilisant un .<br>- `xml`. La valeur est sérialisée à l’aide de la sérialisation XML.<br>- `binary`. La valeur est sérialisée sous forme binaire codé par texte à l’aide de la sérialisation binaire.<br />- `custom`. Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et sérialis et le détonalise. |

## <a name="value-element"></a>\<valeur> élément

Cet élément contient la valeur d’un paramètre.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres d’application et deux paramètres à portée utilisateur :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des paramètres d’application](../../winforms/advanced/application-settings-overview.md)
- [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md)
