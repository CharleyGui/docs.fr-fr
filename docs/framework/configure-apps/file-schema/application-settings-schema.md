---
title: Schéma des paramètres de l’application
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242827"
---
# <a name="application-settings-schema"></a>Schéma des paramètres de l’application

Les paramètres d’application permettent à une application de Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur. Dans ce contexte, un *paramètre* est une information qui peut être spécifique à l’application ou spécifique à l’utilisateur actuel (tout ce qui provient d’une chaîne de connexion de base de données à la taille de fenêtre par défaut préférée de l’utilisateur).

Par défaut, les paramètres d’application d’une application Windows Forms utilisent la <xref:System.Configuration.LocalFileSettingsProvider> classe, qui utilise le système de configuration .net pour stocker les paramètres dans un fichier de configuration XML. Pour plus d’informations sur les fichiers utilisés par les paramètres d’application, consultez [architecture des paramètres d’application](../../winforms/advanced/application-settings-architecture.md).

Les paramètres d’application définissent les éléments suivants dans le cadre des fichiers de configuration qu’il utilise.

| Élément                    | Description                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | Contient toutes les **\<setting>** balises spécifiques à l’application.                         |
| **\<userSettings>**        | Contient toutes les **\<setting>** balises spécifiques à l’utilisateur actuel.                        |
| **\<setting>**             | Définit un paramètre. Enfant de **\<applicationSettings>** ou **\<userSettings>** . |
| **\<value>**               | Définit la valeur d’un paramètre. Enfant de **\<setting>** .                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings>, élément

Cet élément contient toutes les **\<setting>** balises qui sont spécifiques à une instance de l’application sur un ordinateur client. Il ne définit aucun attribut.

## <a name="usersettings-element"></a>\<userSettings>, élément

Cet élément contient toutes les **\<setting>** balises qui sont spécifiques à l’utilisateur qui utilise actuellement l’application. Il ne définit aucun attribut.

## <a name="setting-element"></a>\<setting>, élément

Cet élément définit un paramètre. Il a les attributs suivants.

| Attribut        | Description |
| ---------------- | ----------- |
| **name**         | Obligatoire. ID unique du paramètre. Les paramètres créés par le biais de Visual Studio sont enregistrés avec le nom `ProjectName.Properties.Settings` . |
| **serializeAs** | Obligatoire. Format à utiliser pour sérialiser la valeur dans le texte. Les valeurs autorisées sont :<br><br>- `string`. La valeur est sérialisée sous forme de chaîne à l’aide d’un <xref:System.ComponentModel.TypeConverter> .<br>- `xml`. La valeur est sérialisée à l’aide de la sérialisation XML.<br>- `binary`. La valeur est sérialisée comme binaire encodé en texte à l’aide de la sérialisation binaire.<br />- `custom`. Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et le sérialise et le désérialise. |

## <a name="value-element"></a>\<value>, élément

Cet élément contient la valeur d’un paramètre.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres de portée application et deux paramètres de portée utilisateur :

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
