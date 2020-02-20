---
title: Créer un pack de modèles pour dotnet new
description: Découvrez comment créer un fichier csproj qui générera un pack de modèles pour la commande dotnet new.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5bc926861dd6a501d7c2d24bd5f7c4116cc78b2c
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503493"
---
# <a name="tutorial-create-a-template-pack"></a>Didacticiel : créer un pack de modèles

Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources. Ce didacticiel est la troisième partie d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.

Dans cette partie de la série, vous découvrirez comment :

> [!div class="checklist"]
>
> * Créer un projet \*. csproj pour générer un pack de modèles
> * Configurer le fichier projet pour la compression
> * Installer un modèle à partir d’un fichier NuGet
> * Désinstaller un modèle par ID de package

## <a name="prerequisites"></a>Conditions préalables requises

* Complétez la [première partie](cli-templates-create-item-template.md) et la [deuxième partie](cli-templates-create-project-template.md) de cette série de tutoriels.

  Ce tutoriel utilise les deux modèles créés dans les deux premières parties. Vous pouvez utiliser un autre modèle à condition de copier le modèle, en tant que dossier, dans le dossier _working\templates\\_ .

* Ouvrez un terminal et accédez au dossier de _travail\\_ .

## <a name="create-a-template-pack-project"></a>Créer un projet de pack de modèles

Un pack de modèles correspond à un ou plusieurs modèles empaquetés dans un fichier. Lorsque vous installez ou désinstallez un pack, tous les modèles contenus dans celui-ci sont ajoutés ou supprimés, respectivement. Les parties précédentes de cette série de tutoriels fonctionnaient uniquement avec des modèles individuels. Pour partager un modèle non compressé, vous devez copier le dossier de modèle et l’installer via ce dossier. Étant donné qu’un pack de modèles peut contenir plusieurs modèles, et qu’il s’agit d’un fichier unique, le partage est plus facile.

Les packs de modèles sont représentés par un fichier de package NuGet _(.nupkg)_ . Et, comme n’importe quel package NuGet, vous pouvez télécharger le pack de modèles dans un flux NuGet. La commande `dotnet new -i` prend en charge l’installation du pack de modèles à partir d’un flux de package NuGet. En outre, vous pouvez installer un pack de modèles directement à partir d’un fichier _.nupkg_.

Normalement, vous utilisez un fichier projet C# pour compiler le code et produire un fichier binaire. Toutefois, le projet peut également être utilisé pour générer un pack de modèles. En modifiant les paramètres de _.csproj_, vous pouvez l’empêcher de compiler n’importe quel code et inclure à la place toutes les ressources de vos modèles en tant que ressources. Lorsque ce projet est généré, il génère un package NuGet de pack de modèles.

Le pack que vous allez créer inclut le [modèle d’élément](cli-templates-create-item-template.md) et le [modèle de package](cli-templates-create-project-template.md) créés précédemment. Étant donné que nous avons regroupé les deux modèles dans le dossier _working\templates\\_ , nous pouvons utiliser le dossier _working_ pour le fichier _.csproj_.

Dans votre terminal, accédez au dossier _working_. Créez un nouveau projet et nommez-le `templatepack` et définissez le dossier de sortie sur le dossier actif.

```dotnetcli
dotnet new console -n templatepack -o .
```

Le paramètre `-n` définit le nom de fichier _. csproj_ sur _templatepack. csproj_. Le paramètre `-o` crée les fichiers dans le répertoire actif. Vous devez voir un résultat similaire à la sortie suivante.

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Ensuite, ouvrez le fichier _templatepack.csproj_ dans votre éditeur favori et remplacez le contenu par le code XML suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

Les paramètres `<PropertyGroup>` du code XML ci-dessus sont répartis en trois groupes. Le premier groupe traite des propriétés requises pour un package NuGet. Les trois paramètres `<Package` doivent être définis avec les propriétés du package NuGet pour identifier votre package sur un flux NuGet. Plus précisément, la valeur `<PackageId>` est utilisée pour désinstaller le pack de modèles avec un nom unique et non un chemin d’accès au répertoire. Elle peut également être utilisée pour installer le pack de modèles à partir d’un flux NuGet. Les autres paramètres, `<Title>` et `<PackageTags>`, sont associés aux métadonnées affichées sur le flux NuGet. Pour plus d’informations sur les paramètres NuGet, consultez [Propriétés NuGet et MSBuild](/nuget/reference/msbuild-targets).

Le paramètre `<TargetFramework>` doit être défini de sorte que MSBuild s’exécute correctement quand vous exécutez la commande pack pour compiler et empaqueter le projet.

Les trois derniers paramètres concernent la configuration correcte du projet pour inclure les modèles dans le dossier approprié du pack NuGet lors de sa création.

`<ItemGroup>` contient deux paramètres. Tout d’abord, le paramètre `<Content>` inclut l’ensemble du dossier _templates_ en tant que contenu. Il est également défini pour exclure tout dossier _bin_ ou _obj_ pour empêcher l’inclusion de code compilé (si vous avez testé et compilé vos modèles). Ensuite, le paramètre `<Compile>` exclut la compilation de tous les fichiers de code, quel que soit l’emplacement où ils se trouvent. Ce paramètre empêche le projet utilisé pour créer un pack de modèles d’essayer de compiler le code dans la hiérarchie des dossiers _templates_.

## <a name="build-and-install"></a>Générer et installer

Enregistrer ce fichier, puis exécuter la commande pack

```dotnetcli
dotnet pack
```

Cette commande génère votre projet et crée un package NuGet dans le dossier _working\bin\Debug_.

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Ensuite, installez le fichier de pack de modèles avec la commande `dotnet new -i PATH_TO_NUPKG_FILE`.

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

Si vous avez chargé le package NuGet dans un flux NuGet, vous pouvez utiliser la commande `dotnet new -i PACKAGEID`, où `PACKAGEID` est identique au paramètre `<PackageId>` du fichier _.csproj_. Cet ID de package est identique à l’identificateur du package NuGet.

## <a name="uninstall-the-template-pack"></a>Désinstaller le pack de modèles

Quelle que soit la façon dont vous avez installé le pack de modèles, directement avec le fichier _.nupkg_ ou avec le flux NuGet, la suppression d’un pack de modèles est identique. Utilisez `<PackageId>` du modèle à désinstaller. Vous pouvez obtenir la liste des modèles installés en exécutant la commande `dotnet new -u`.

```dotnetcli
dotnet new -u
```

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
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

Exécutez `dotnet new -u AdatumCorporation.Utility.Templates` pour désinstaller le modèle. La commande `dotnet new` génère des informations d’aide qui doivent omettre les modèles que vous avez installés précédemment.

Félicitations ! Vous avez installé et désinstallé un pack de modèles.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les modèles, consultez l’article [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).

* [Wiki du dépôt GitHub dotnet/templating](https://github.com/dotnet/templating/wiki)
* [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
* [Schéma *template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template)
