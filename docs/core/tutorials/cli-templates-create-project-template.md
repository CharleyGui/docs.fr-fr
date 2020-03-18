---
title: Créer un modèle de projet pour dotnet new
description: Découvrez comment créer un modèle de projet pour la commande dotnet new.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503532"
---
# <a name="tutorial-create-a-project-template"></a>Tutorial: Créer un modèle de projet

Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources. Ce tutoriel est le deuxième d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.

Dans cette partie de la série, vous découvrirez comment :

> [!div class="checklist"]
>
> * Créer les ressources d’un modèle de projet
> * Créer le dossier et le fichier de configuration du modèle
> * Installer un modèle à partir d’un chemin de fichier
> * Tester un modèle d’élément
> * Désinstaller un modèle d'élément

## <a name="prerequisites"></a>Conditions préalables requises

* Complétez la [première partie](cli-templates-create-item-template.md) de cette série de tutoriels.
* Ouvrez un terminal et accédez au dossier _working\templates_.

## <a name="create-a-project-template"></a>Créer un modèle de projet

Les modèles de projet produisent des projets prêts à être exécutés, qui permettent aux utilisateurs de démarrer facilement avec un jeu de code fonctionnel. .NET Core comprend quelques modèles de projet, tels qu’une application console ou une bibliothèque de classes. Dans cet exemple, vous allez créer un nouveau projet console qui active C# 8.0 et génère un point d’entrée `async main`.

Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _consoleasync_. Entrez dans le sous-dossier et exécutez `dotnet new console` pour générer l’application console standard. Vous allez modifier les fichiers générés par ce modèle pour créer un nouveau modèle.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Modifier Program.cs

Ouvrez le fichier _program.cs_. Le projet console n’utilise pas de point d’entrée asynchrone, nous allons donc l’ajouter. Modifiez votre code pour savoir ce qui suit et enregistrez le fichier.

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Modifier consoleasync.csproj

Nous allons mettre à jour vers la version 8.0 la version de langage C# que le projet utilise. Modifiez le fichier _consoleasync.csproj_ et ajoutez le paramètre `<LangVersion>` à un nœud `<PropertyGroup>`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Créer le projet

Avant de terminer un modèle de projet, vous devez le tester pour vous assurer qu’il se compile et s’exécute correctement.

Dans votre terminal, exécutez la commande suivante.

```dotnetcli
dotnet run
```

Vous obtenez la sortie suivante.

```console
Hello World with C# 8.0!
```

Vous pouvez supprimer les dossiers _obj_ et _bin_ créés à l’aide de `dotnet run`. La suppression de ces fichiers garantit que votre modèle inclue uniquement les fichiers associés à votre modèle et pas les fichiers qui résultent d’une action de génération.

Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.

## <a name="create-the-template-config"></a>Créer la configuration du modèle

Les modèles sont reconnus dans .NET Core par un dossier et un fichier de configuration spécifiques qui se trouvent à la racine de votre modèle. Dans ce tutoriel, votre dossier de modèle se trouve dans _working\templates\consoleasync_.

Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial. Ce dossier de configuration est nommé _.template.config_.

Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y. Créez ensuite un nouveau fichier nommé _template.json_. Votre structure de dossier devrait ressembler à ceci.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Ouvrez le _template.json_ avec votre éditeur de texte préféré et collez dans le code json suivant et enregistrez-le.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Ce fichier de configuration contient tous les paramètres de votre modèle. Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `project`. Cela désigne votre modèle en tant que modèle de projet. Il n’existe aucune restriction sur le type de modèle que vous créez. Les valeurs `item` et `project` sont des noms courants que .NET Core recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.

L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles. Les utilisateurs peuvent également effectuer une recherche sur les balises de classification. Ne confondez pas la propriété `tags` dans le fichier json avec la liste de balises `classifications`. Il s’agit de deux choses différentes, qui ont malheureusement le même nom. Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template). Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).

Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé. Avant d’installer le modèle, veillez à supprimer tous les fichiers et dossiers supplémentaires que vous ne souhaitez pas inclure dans votre modèle, comme les dossiers _bin_ ou _obj_. Dans votre terminal, accédez au dossier _consoleasync_ et exécutez `dotnet new -i .\` pour installer le modèle situé dans le dossier actuel. Si vous utilisez un système d’exploitation Linux ou `dotnet new -i ./`macOS, utilisez une barre oblique avant : .

Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.

```dotnetcli
dotnet new -i .\
```

Vous obtenez la sortie similaire à ce qui suit.

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a>Tester le modèle de projet

Maintenant que vous avez un modèle d’élément installé, testez-le.

1. Naviguez vers le dossier _d’essai_

1. Créez une nouvelle application de console avec la commande suivante qui `dotnet run` génère un projet de travail que vous pouvez facilement tester avec la commande.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Vous obtenez la sortie suivante.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Exécutez le projet à l’aide de la commande suivante.

    ```dotnetcli
    dotnet run
    ```

    Vous obtenez la sortie suivante.

    ```console
    Hello World with C# 8.0!
    ```

Félicitations ! Vous avez créé et déployé un modèle de projet avec .NET Core. Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé. Veillez à supprimer également tous les fichiers du dossier _test_. Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.

### <a name="uninstall-the-template"></a>Désinstaller le modèle

Étant donné que vous avez installé le modèle avec un chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**. Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`. Votre modèle doit être listé en dernier. Utilisez le chemin indiqué pour désinstaller votre modèle à l’aide de la commande `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.

```dotnetcli
dotnet new -u
```

Vous obtenez la sortie similaire à ce qui suit.

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

Pour désinstaller un modèle, exécutez la commande suivante.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un modèle de projet. Pour savoir comment empaqueter les modèles d’élément et de projet dans un fichier facile à utiliser, poursuivez cette série de tutoriels.

> [!div class="nextstepaction"]
> [Créer un pack de modèles](cli-templates-create-template-pack.md)
