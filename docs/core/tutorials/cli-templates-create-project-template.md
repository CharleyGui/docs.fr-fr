---
title: Créer un modèle de projet pour dotnet new
description: Découvrez comment créer un modèle de projet pour la commande dotnet new.
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: ed40cfd303c70c7b8f198a0f5b593bf1e1ebeaf8
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513131"
---
# <a name="tutorial-create-a-project-template"></a>Didacticiel : créer un modèle de projet

Avec .NET, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources. Ce tutoriel est le deuxième d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.

Dans cette partie de la série, vous découvrirez comment :

> [!div class="checklist"]
>
> * Créer les ressources d’un modèle de projet
> * Créer le dossier et le fichier de configuration du modèle
> * Installer un modèle à partir d’un chemin de fichier
> * Tester un modèle d’élément
> * Désinstaller un modèle d'élément

## <a name="prerequisites"></a>Prérequis

* Complétez la [première partie](cli-templates-create-item-template.md) de cette série de tutoriels.
* Ouvrez un terminal et accédez au dossier _working\templates_.

## <a name="create-a-project-template"></a>Créer un modèle de projet

Les modèles de projet produisent des projets prêts à être exécutés, qui permettent aux utilisateurs de démarrer facilement avec un jeu de code fonctionnel. .NET comprend quelques modèles de projet, tels qu’une application console ou une bibliothèque de classes. Dans cet exemple, vous allez créer un nouveau projet de console qui active C# 9,0 et génère un `async main` point d’entrée.

Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _consoleasync_. Entrez dans le sous-dossier et exécutez `dotnet new console` pour générer l’application console standard. Vous allez modifier les fichiers générés par ce modèle pour créer un nouveau modèle.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Modifier Program.cs

Ouvrez le fichier _program.cs_. Le projet console n’utilise pas de point d’entrée asynchrone, nous allons donc l’ajouter. Remplacez votre code par ce qui suit et enregistrez le fichier.

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 9.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Modifier consoleasync.csproj

Nous allons mettre à jour la version du langage C# que le projet utilise pour la version 9,0. Modifiez le fichier _consoleasync.csproj_ et ajoutez le paramètre `<LangVersion>` à un nœud `<PropertyGroup>`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>

    <LangVersion>9.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Créer le projet

Avant de terminer un modèle de projet, vous devez le tester pour vous assurer qu’il se compile et s’exécute correctement.

Dans votre terminal, exécutez la commande suivante.

```dotnetcli
dotnet run
```

Vous recevez la sortie suivante.

```console
Hello World with C# 9.0!
```

Vous pouvez supprimer les dossiers _obj_ et _bin_ créés à l’aide de `dotnet run`. La suppression de ces fichiers garantit que votre modèle comprend uniquement les fichiers associés à votre modèle, et non les fichiers qui résultent d’une action de génération.

Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.

## <a name="create-the-template-config"></a>Créer la configuration du modèle

Les modèles sont reconnus dans .NET par un dossier spécial et un fichier de configuration qui se trouvent à la racine de votre modèle. Dans ce tutoriel, votre dossier de modèle se trouve dans _working\templates\consoleasync_.

Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial. Ce dossier de configuration est nommé _.template.config_.

Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y. Créez ensuite un nouveau fichier nommé _template.json_. Votre structure de dossiers doit ressembler à ceci.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Ouvrez le _template.jsdans_ avec votre éditeur de texte préféré et collez le code JSON suivant et enregistrez-le.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#9" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Ce fichier de configuration contient tous les paramètres de votre modèle. Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `project`. Cela désigne votre modèle en tant que modèle de projet. Il n’existe aucune restriction sur le type de modèle que vous créez. Les `item` `project` valeurs et sont des noms communs que .net recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.

L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles. Les utilisateurs peuvent également effectuer une recherche sur les balises de classification. Ne confondez pas la propriété `tags` dans le fichier json avec la liste de balises `classifications`. Il s’agit de deux choses différentes, qui ont malheureusement le même nom. Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template). Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).

Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé. Avant d’installer le modèle, veillez à supprimer tous les fichiers et dossiers supplémentaires que vous ne souhaitez pas inclure dans votre modèle, comme les dossiers _bin_ ou _obj_. Dans votre terminal, accédez au dossier _consoleasync_ et exécutez `dotnet new -i .\` pour installer le modèle situé dans le dossier actuel. Si vous utilisez un système d’exploitation Linux ou macOS, utilisez une barre oblique : `dotnet new -i ./` .

Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.

```dotnetcli
dotnet new -i .\
```

Vous recevez une sortie similaire à ce qui suit.

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

### <a name="test-the-project-template"></a>Tester le modèle de projet

Maintenant que vous avez un modèle de projet installé, testez-le.

1. Accéder au dossier de _test_

1. Créez une application console à l’aide de la commande suivante, qui génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la `dotnet run` commande.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Vous recevez la sortie suivante.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Exécutez le projet à l’aide de la commande suivante.

    ```dotnetcli
    dotnet run
    ```

    Vous recevez la sortie suivante.

    ```console
    Hello World with C# 9.0!
    ```

Félicitations ! Vous avez créé et déployé un modèle de projet avec .NET. Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé. Veillez à supprimer également tous les fichiers du dossier _test_. Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.

### <a name="uninstall-the-template"></a>Désinstaller le modèle

Étant donné que vous avez installé le modèle avec un chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**. Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`. Votre modèle doit être listé en dernier. Utilisez la `Uninstall Command` liste pour désinstaller votre modèle.

```dotnetcli
dotnet new -u
```

Vous recevez une sortie similaire à ce qui suit.

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

  C:\Test\templatetutorial\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\consoleasync
```

Pour désinstaller le modèle que vous avez créé, exécutez le `Uninstall Command` qui est affiché dans la sortie.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un modèle de projet. Pour savoir comment empaqueter les modèles d’élément et de projet dans un fichier facile à utiliser, poursuivez cette série de tutoriels.

> [!div class="nextstepaction"]
> [Créer un pack de modèles](cli-templates-create-template-pack.md)
