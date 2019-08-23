---
title: <appSettings>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: a64db49b521651ccff8b928720fe3273f8600b68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921322"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > élément pour \<la configuration >

Contient des paramètres d’application personnalisés. Il s’agit d’une section de configuration prédéfinie fournie par le .NET Framework.

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **fichier**  | Attribut facultatif.<br><br>Spécifie un chemin d’accès relatif à un fichier externe contenant les paramètres de configuration d’application personnalisés. Le fichier spécifié contient le même type de paramètres que ceux spécifiés dans les  **\<éléments Add >** ,  **\<Remove >** et  **\<Clear >** et utilise le même format de paire clé/valeur que ces éléments.<br><br>Le chemin d’accès spécifié est relatif au fichier de configuration principal. Pour une application Windows Forms, il s’agit du dossier binaire (tel que */bin/debug*), et non de l’emplacement du fichier de configuration de l’application. Pour les applications Web Forms, le chemin d’accès est relatif à la racine de l’application, où se trouve le fichier *Web. config* .<br><br>Notez que le runtime ignore l’attribut si le fichier spécifié est introuvable. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [élément de > de configuration  **\<** ](../configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<add>** ](add-element-for-appsettings.md) | Ajoute un paramètre d’application personnalisé. |
| [ **\<clear>** ](clear-element-for-appsettings.md) | Efface tous les paramètres d’application précédemment définis. |
| [ **\<remove>** ](remove-element-for-appsettings.md) | Supprime un paramètre d’application défini précédemment. |

## <a name="remarks"></a>Notes

L’élément > appSettings stocke des informations de configuration d’application personnalisées, telles que des chaînes de connexion de base de données, des chemins de fichier, des URL de service Web XML ou d’autres informations de configuration personnalisée pour une application.  **\<** Les paires clé/valeur spécifiées dans l' <xref:System.Configuration.ConfigurationSettings>  **\<élément > appSettings** sont accessibles dans le code à l’aide de la classe.

Vous pouvez utiliser l’attribut de **fichier** dans l'  **\<élément de > appSettings** des fichiers *Web. config* et de configuration de l’application. Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou substitue les paramètres spécifiés dans l'  **\<élément > appSettings** . L’attribut de **fichier** peut être utilisé dans les scénarios de développement de l’équipe de contrôle de code source, par exemple lorsqu’un utilisateur souhaite remplacer les paramètres de projet spécifiés dans un fichier de configuration de l’application.

Les fichiers de configuration spécifiés par l’attribut **file** doivent avoir un nœud racine de  **\<appSettings >** plutôt que des  **\<> de configuration**.

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

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](../index.md)
