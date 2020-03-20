---
title: <appSettings>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155529"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings> élément pour \<la configuration>

Contient des paramètres d’application personnalisés. Il s’agit d’une section de configuration prédéfinie fournie par le cadre .NET.

configuration &nbsp; &nbsp;>[** \<**](../configuration-element.md) ** \<appSettings>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **Fichier**  | Attribut facultatif.<br><br>Spécifie un chemin relatif vers un fichier externe contenant des paramètres de configuration d’application personnalisés. Le fichier spécifié contient le même type de paramètres qui sont spécifiés dans ** \<l’ajout>**, ** \<supprimer>**, et ** \<effacer>** éléments et utilise le même format de paire de clé / valeur que ces éléments.<br><br>Le chemin spécifié est relatif au fichier de configuration principal. Pour une application Windows Forms, il s’agit du dossier binaire (tel que */bin/debug),* et non de l’emplacement du fichier de configuration d’application. Pour les applications Web Forms, le chemin est relatif à la racine de l’application, où se trouve le fichier *web.config.*<br><br>Le temps d’exécution ignore l’attribut si le fichier spécifié ne peut pas être trouvé. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [** \<configuration>** Élément](../configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<ajouter>**](add-element-for-appsettings.md) | Ajoute un paramètre d’application personnalisé. |
| [**\<clair>**](clear-element-for-appsettings.md) | Efface tous les paramètres d’application précédemment définis. |
| [**\<supprimer>**](remove-element-for-appsettings.md) | Supprime un paramètre d’application précédemment défini. |

## <a name="remarks"></a>Notes 

Les ** \<appSettings>** élément stockent des informations personnalisées sur la configuration des applications, telles que les chaînes de connexion de base de données, les trajectoires de fichiers, les URL du service Web XML ou toute autre information de configuration personnalisée pour une application. Les paires de clés/valeurs spécifiées dans les <xref:System.Configuration.ConfigurationSettings> ** \<appSettings>** élément sont accessibles dans le code à l’aide de la classe.

Vous pouvez utiliser l’attribut **de fichier** dans les ** \<appSettings>** élément des fichiers *Web.config* et configuration d’application. Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou remplace les paramètres spécifiés dans les ** \<appSettings>** élément. **L’attribut de fichier** peut être utilisé dans les scénarios de développement de l’équipe de contrôle source, par exemple lorsqu’un utilisateur souhaite remplacer les paramètres du projet spécifiés dans un fichier de configuration d’application.

Les fichiers de configuration spécifiés par l’attribut de **fichier** doivent avoir un nœud de racine des ** \<appSettings>** plutôt que ** \<la configuration>**.

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

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.

## <a name="see-also"></a>Voir aussi

- [Schéma de fichier de configuration pour le cadre .NET](../index.md)
