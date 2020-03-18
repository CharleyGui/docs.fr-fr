---
title: Créer un modèle d’élément pour la commande dotnet new - CLI .NET Core
description: Découvrez comment créer un modèle d’élément pour la commande dotnet new. Les modèles d’élément peuvent contenir n’importe quel nombre de fichiers.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503559"
---
# <a name="tutorial-create-an-item-template"></a>Tutorial: Créer un modèle d’élément

Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources. Ce tutoriel est le premier d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.

Dans cette partie de la série, vous découvrirez comment :

> [!div class="checklist"]
>
> * Créer une classe pour un modèle d’élément
> * Créer le dossier et le fichier de configuration du modèle
> * Installer un modèle à partir d’un chemin de fichier
> * Tester un modèle d’élément
> * Désinstaller un modèle d'élément

## <a name="prerequisites"></a>Conditions préalables requises

* [SDK .NET Core 2.2](https://dotnet.microsoft.com/download) ou versions ultérieures.
* Lisez l’article de référence [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).

  L’article de référence explique les notions de base sur les modèles et la façon dont ils sont créés. Certaines de ces informations seront répétées ici.

* Ouvrez un terminal et accédez au dossier _working\templates_.

## <a name="create-the-required-folders"></a>Créer les dossiers requis

Cette série utilise un « dossier de travail » dans lequel se trouve votre source de modèle et un « dossier de test » utilisé pour tester vos modèles. Le dossier de travail et le dossier de test doivent se trouver sous le même dossier parent.

Tout d’abord, créez le dossier parent, le nom n’a pas d’importance. Puis, créez un sous-dossier nommé _working_. Dans le dossier _working_, créez un sous-dossier nommé _templates_.

Ensuite, créez un dossier sous le dossier parent nommé _test_. La structure du dossier doit ressembler à ce qui suit.

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Créer un modèle d’élément

Un modèle d’élément est un type spécifique de modèle qui contient un ou plusieurs fichiers. Ces types de modèles sont utiles lorsque vous souhaitez générer un fichier de configuration, de code ou de solution. Dans cet exemple, vous allez créer une classe qui ajoute une méthode d’extension au type de chaîne.

Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _extensions_. Entrez dans le dossier.

```console
working
└───templates
    └───extensions
```

Créez un nouveau fichier nommé _CommonExtensions.cs_ et ouvrez-le avec votre éditeur de texte favori. Cette classe fournit une méthode d’extension nommée `Reverse` qui inverse le contenu d’une chaîne. Collez le code suivant et enregistrez le fichier :

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.

## <a name="create-the-template-config"></a>Créer la configuration du modèle

Les modèles sont reconnus dans .NET Core par un dossier et un fichier de configuration spécifiques qui se trouvent à la racine de votre modèle. Dans ce tutoriel, votre dossier de modèle se trouve dans _working\templates\extensions_.

Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial. Ce dossier de configuration est nommé _.template.config_.

Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y. Créez ensuite un nouveau fichier nommé _template.json_. La structure des dossiers doit ressembler à ceci :

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Ouvrez le _template.json_ avec votre éditeur de texte préféré et collez dans le code JSON suivant et enregistrez-le.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

Ce fichier de configuration contient tous les paramètres de votre modèle. Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `item`. Cela classe votre modèle en tant que modèle d’élément. Il n’existe aucune restriction sur le type de modèle que vous créez. Les valeurs `item` et `project` sont des noms courants que .NET Core recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.

L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles. Les utilisateurs peuvent également effectuer une recherche sur les balises de classification. Ne confondez pas la propriété `tags` dans le fichier \*.json avec la liste de balises `classifications`. Il s’agit de deux choses différentes, qui ont malheureusement le même nom. Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template). Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).

Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé. Dans votre terminal, accédez au dossier _extensions_ et exécutez la commande suivante pour installer le modèle situé dans le dossier actuel :

* **Sur Windows**:`dotnet new -i .\`
* **Sur Linux ou macOS**:`dotnet new -i ./`

Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>Tester le modèle d’élément

Maintenant que vous avez un modèle d’élément installé, testez-le. Accédez au dossier _test/_ et créez une application console avec `dotnet new console`. Cela génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la commande `dotnet run`.

```dotnetcli
dotnet new console
```

Vous obtenez la sortie similaire à ce qui suit.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

Exécuter le projet avec.

```dotnetcli
dotnet run
```

Vous obtenez la sortie suivante.

```console
Hello World!
```

Ensuite, exécutez `dotnet new stringext` pour générer _CommonExtensions.cs_ à partir du modèle.

```dotnetcli
dotnet new stringext
```

Vous obtenez la sortie suivante.

```console
The template "Example templates: string extensions" was created successfully.
```

Modifiez le code dans _Program.cs_ pour inverser la chaîne `"Hello World"` avec la méthode d’extension fournie par le modèle.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Réexécutez le programme et vous verrez que le résultat est inversé.

```dotnetcli
dotnet run
```

Vous obtenez la sortie suivante.

```console
!dlroW olleH
```

Félicitations ! Vous avez créé et déployé un modèle d’élément avec .NET Core. Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé. Veillez à supprimer également tous les fichiers du dossier _test_. Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.

## <a name="uninstall-the-template"></a>Désinstaller le modèle

Étant donné que vous avez installé le modèle par chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**. Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`. Votre modèle doit être listé en dernier. Utilisez le chemin indiqué pour désinstaller votre modèle à l’aide de la commande `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

Pour désinstaller un modèle, exécutez la commande suivante.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un modèle d’élément. Pour savoir comment créer un modèle de projet, poursuivez cette série de tutoriels.

> [!div class="nextstepaction"]
> [Créer un modèle de projet](cli-templates-create-project-template.md)
