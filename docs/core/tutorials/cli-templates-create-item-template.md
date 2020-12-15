---
title: Créer un modèle d’élément pour dotnet New-.NET CLI
description: Découvrez comment créer un modèle d’élément pour la commande dotnet new. Les modèles d’élément peuvent contenir n’importe quel nombre de fichiers.
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: b148870480584cff37f3fd395e0594344001f247
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512422"
---
# <a name="tutorial-create-an-item-template"></a>Didacticiel : créer un modèle d’élément

Avec .NET, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources. Ce didacticiel fait partie d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la `dotnet new` commande.

Dans cette partie de la série, vous découvrirez comment :

> [!div class="checklist"]
>
> * Créer une classe pour un modèle d’élément
> * Créer le dossier et le fichier de configuration du modèle
> * Installer un modèle à partir d’un chemin de fichier
> * Tester un modèle d’élément
> * Désinstaller un modèle d'élément

## <a name="prerequisites"></a>Prérequis

* [.Net 5,0 SDK](https://dotnet.microsoft.com/download) ou une version ultérieure.
* Lisez l’article de référence [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).

  L’article de référence explique les notions de base sur les modèles et la façon dont ils sont créés. Certaines de ces informations seront répétées ici.

* Ouvrez un terminal et accédez au dossier _working\templates_.

## <a name="create-the-required-folders"></a>Créer les dossiers requis

Cette série utilise un « dossier de travail » dans lequel se trouve votre source de modèle et un « dossier de test » utilisé pour tester vos modèles. Le dossier de travail et le dossier de test doivent se trouver sous le même dossier parent.

Tout d’abord, créez le dossier parent, le nom n’a pas d’importance. Puis, créez un sous-dossier nommé _working_. Dans le dossier _working_, créez un sous-dossier nommé _templates_.

Ensuite, créez un dossier sous le dossier parent nommé _test_. La structure des dossiers doit ressembler à ce qui suit.

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

Les modèles sont reconnus par un dossier spécial et un fichier de configuration qui se trouvent à la racine de votre modèle. Dans ce tutoriel, votre dossier de modèle se trouve dans _working\templates\extensions_.

Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial. Ce dossier de configuration est nommé _.template.config_.

Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y. Créez ensuite un nouveau fichier nommé _template.json_. La structure des dossiers doit ressembler à ceci :

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Ouvrez le _template.jsdans_ avec votre éditeur de texte préféré et collez le code JSON suivant et enregistrez-le.

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

Ce fichier de configuration contient tous les paramètres de votre modèle. Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `item`. Cela classe votre modèle en tant que modèle d’élément. Il n’existe aucune restriction sur le type de modèle que vous créez. Les `item` `project` valeurs et sont des noms communs que .net recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.

L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles. Les utilisateurs peuvent également effectuer une recherche sur les balises de classification. Ne confondez pas la propriété `tags` dans le fichier \*.json avec la liste de balises `classifications`. Il s’agit de deux choses différentes, qui ont malheureusement le même nom. Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template). Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).

Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé. Dans votre terminal, accédez au dossier _extensions_ et exécutez la commande suivante pour installer le modèle situé dans le dossier actuel :

* **Sur Windows**: `dotnet new -i .\`
* **Sur Linux ou MacOS**: `dotnet new -i ./`

Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Example templates: string extensions              stringext                [C#]              Common/Code
Console Application                               console                  [C#], F#, VB      Common/Console
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

## <a name="test-the-item-template"></a>Tester le modèle d’élément

Maintenant que vous avez un modèle d’élément installé, testez-le. Accédez au dossier _test/_ et créez une application console avec `dotnet new console`. Cela génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la commande `dotnet run`.

```dotnetcli
dotnet new console
```

Vous recevez une sortie similaire à ce qui suit.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

Exécutez le projet avec.

```dotnetcli
dotnet run
```

Vous recevez la sortie suivante.

```console
Hello World!
```

Ensuite, exécutez `dotnet new stringext` pour générer _CommonExtensions.cs_ à partir du modèle.

```dotnetcli
dotnet new stringext
```

Vous recevez la sortie suivante.

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

Vous recevez la sortie suivante.

```console
!dlroW olleH
```

Félicitations ! Vous avez créé et déployé un modèle d’élément avec .NET. Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé. Veillez à supprimer également tous les fichiers du dossier _test_. Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.

## <a name="uninstall-the-template"></a>Désinstaller le modèle

Étant donné que vous avez installé le modèle par chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**. Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`. Votre modèle doit être listé en dernier. Utilisez la `Uninstall Command` liste pour désinstaller votre modèle.

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

C:\Test\templatetutorial\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\extensions
```

Pour désinstaller le modèle que vous avez créé, exécutez le `Uninstall Command` qui est affiché dans la sortie.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un modèle d’élément. Pour savoir comment créer un modèle de projet, poursuivez cette série de tutoriels.

> [!div class="nextstepaction"]
> [Créer un modèle de projet](cli-templates-create-project-template.md)
