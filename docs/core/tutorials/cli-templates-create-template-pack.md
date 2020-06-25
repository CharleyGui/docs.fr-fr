---
title: Créer un pack de modèles pour dotnet new
description: Découvrez comment créer un fichier csproj qui générera un pack de modèles pour la commande dotnet new.
author: adegeo
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 25264fff42c47f5bb660f68f85dbb123b5b2608c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324327"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="0af3f-103">Didacticiel : créer un pack de modèles</span><span class="sxs-lookup"><span data-stu-id="0af3f-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="0af3f-104">Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources.</span><span class="sxs-lookup"><span data-stu-id="0af3f-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="0af3f-105">Ce didacticiel est la troisième partie d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la `dotnet new` commande.</span><span class="sxs-lookup"><span data-stu-id="0af3f-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="0af3f-106">Dans cette partie de la série, vous découvrirez comment :</span><span class="sxs-lookup"><span data-stu-id="0af3f-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0af3f-107">Créer un \* projet. csproj pour générer un pack de modèles</span><span class="sxs-lookup"><span data-stu-id="0af3f-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="0af3f-108">Configurer le fichier projet pour la compression</span><span class="sxs-lookup"><span data-stu-id="0af3f-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="0af3f-109">Installer un modèle à partir d’un fichier NuGet</span><span class="sxs-lookup"><span data-stu-id="0af3f-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="0af3f-110">Désinstaller un modèle par ID de package</span><span class="sxs-lookup"><span data-stu-id="0af3f-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0af3f-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0af3f-111">Prerequisites</span></span>

* <span data-ttu-id="0af3f-112">Complétez la [première partie](cli-templates-create-item-template.md) et la [deuxième partie](cli-templates-create-project-template.md) de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="0af3f-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="0af3f-113">Ce tutoriel utilise les deux modèles créés dans les deux premières parties.</span><span class="sxs-lookup"><span data-stu-id="0af3f-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="0af3f-114">Vous pouvez utiliser un autre modèle à condition de copier le modèle, en tant que dossier, dans le _dossier \\ working\templates_ .</span><span class="sxs-lookup"><span data-stu-id="0af3f-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="0af3f-115">Ouvrez un terminal et accédez au dossier _de \\ travail_ .</span><span class="sxs-lookup"><span data-stu-id="0af3f-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="0af3f-116">Créer un projet de pack de modèles</span><span class="sxs-lookup"><span data-stu-id="0af3f-116">Create a template pack project</span></span>

<span data-ttu-id="0af3f-117">Un pack de modèles correspond à un ou plusieurs modèles empaquetés dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="0af3f-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="0af3f-118">Lorsque vous installez ou désinstallez un pack, tous les modèles contenus dans celui-ci sont ajoutés ou supprimés, respectivement.</span><span class="sxs-lookup"><span data-stu-id="0af3f-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="0af3f-119">Les parties précédentes de cette série de tutoriels fonctionnaient uniquement avec des modèles individuels.</span><span class="sxs-lookup"><span data-stu-id="0af3f-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="0af3f-120">Pour partager un modèle non compressé, vous devez copier le dossier de modèle et l’installer via ce dossier.</span><span class="sxs-lookup"><span data-stu-id="0af3f-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="0af3f-121">Étant donné qu’un pack de modèles peut contenir plusieurs modèles, et qu’il s’agit d’un fichier unique, le partage est plus facile.</span><span class="sxs-lookup"><span data-stu-id="0af3f-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="0af3f-122">Les packs de modèles sont représentés par un fichier de package NuGet _(.nupkg)_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="0af3f-123">Et, comme n’importe quel package NuGet, vous pouvez télécharger le pack de modèles dans un flux NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="0af3f-124">La commande `dotnet new -i` prend en charge l’installation du pack de modèles à partir d’un flux de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="0af3f-125">En outre, vous pouvez installer un pack de modèles directement à partir d’un fichier _.nupkg_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="0af3f-126">Normalement, vous utilisez un fichier projet C# pour compiler le code et produire un fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="0af3f-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="0af3f-127">Toutefois, le projet peut également être utilisé pour générer un pack de modèles.</span><span class="sxs-lookup"><span data-stu-id="0af3f-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="0af3f-128">En modifiant les paramètres de _.csproj_, vous pouvez l’empêcher de compiler n’importe quel code et inclure à la place toutes les ressources de vos modèles en tant que ressources.</span><span class="sxs-lookup"><span data-stu-id="0af3f-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="0af3f-129">Lorsque ce projet est généré, il génère un package NuGet de pack de modèles.</span><span class="sxs-lookup"><span data-stu-id="0af3f-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="0af3f-130">Le pack que vous allez créer inclut le [modèle d’élément](cli-templates-create-item-template.md) et le [modèle de package](cli-templates-create-project-template.md) créés précédemment.</span><span class="sxs-lookup"><span data-stu-id="0af3f-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="0af3f-131">Étant donné que nous avons regroupé les deux modèles dans le dossier _working\templates\\_, nous pouvons utiliser le dossier _working_ pour le fichier _.csproj_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="0af3f-132">Dans votre terminal, accédez au dossier _working_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="0af3f-133">Créez un nouveau projet et nommez-le `templatepack` et définissez le dossier de sortie sur le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="0af3f-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="0af3f-134">Le `-n` paramètre définit le nom de fichier _. csproj_ sur _templatepack. csproj_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="0af3f-135">Le `-o` paramètre crée les fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0af3f-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="0af3f-136">Vous devez voir un résultat similaire à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="0af3f-136">You should see a result similar to the following output.</span></span>

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

<span data-ttu-id="0af3f-137">Ensuite, ouvrez le fichier _templatepack.csproj_ dans votre éditeur favori et remplacez le contenu par le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0af3f-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="0af3f-138">Les paramètres `<PropertyGroup>` du code XML ci-dessus sont répartis en trois groupes.</span><span class="sxs-lookup"><span data-stu-id="0af3f-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="0af3f-139">Le premier groupe traite des propriétés requises pour un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="0af3f-140">Les trois paramètres `<Package` doivent être définis avec les propriétés du package NuGet pour identifier votre package sur un flux NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-140">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="0af3f-141">Plus précisément, la valeur `<PackageId>` est utilisée pour désinstaller le pack de modèles avec un nom unique et non un chemin d’accès au répertoire.</span><span class="sxs-lookup"><span data-stu-id="0af3f-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="0af3f-142">Elle peut également être utilisée pour installer le pack de modèles à partir d’un flux NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="0af3f-143">Les autres paramètres, `<Title>` et `<PackageTags>`, sont associés aux métadonnées affichées sur le flux NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="0af3f-144">Pour plus d’informations sur les paramètres NuGet, consultez [Propriétés NuGet et MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="0af3f-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="0af3f-145">Le paramètre `<TargetFramework>` doit être défini de sorte que MSBuild s’exécute correctement quand vous exécutez la commande pack pour compiler et empaqueter le projet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="0af3f-146">Les trois derniers paramètres concernent la configuration correcte du projet pour inclure les modèles dans le dossier approprié du pack NuGet lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="0af3f-146">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="0af3f-147">`<ItemGroup>` contient deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="0af3f-147">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="0af3f-148">Tout d’abord, le paramètre `<Content>` inclut l’ensemble du dossier _templates_ en tant que contenu.</span><span class="sxs-lookup"><span data-stu-id="0af3f-148">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="0af3f-149">Il est également défini pour exclure tout dossier _bin_ ou _obj_ pour empêcher l’inclusion de code compilé (si vous avez testé et compilé vos modèles).</span><span class="sxs-lookup"><span data-stu-id="0af3f-149">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="0af3f-150">Ensuite, le paramètre `<Compile>` exclut la compilation de tous les fichiers de code, quel que soit l’emplacement où ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="0af3f-150">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="0af3f-151">Ce paramètre empêche le projet utilisé pour créer un pack de modèles d’essayer de compiler le code dans la hiérarchie des dossiers _templates_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-151">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="0af3f-152">Générer et installer</span><span class="sxs-lookup"><span data-stu-id="0af3f-152">Build and install</span></span>

<span data-ttu-id="0af3f-153">Enregistrer ce fichier, puis exécuter la commande pack</span><span class="sxs-lookup"><span data-stu-id="0af3f-153">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="0af3f-154">Cette commande génère votre projet et crée un package NuGet dans le dossier _working\bin\Debug_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-154">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

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

<span data-ttu-id="0af3f-155">Ensuite, installez le fichier de pack de modèles avec la commande `dotnet new -i PATH_TO_NUPKG_FILE`.</span><span class="sxs-lookup"><span data-stu-id="0af3f-155">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

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

<span data-ttu-id="0af3f-156">Si vous avez chargé le package NuGet dans un flux NuGet, vous pouvez utiliser la commande `dotnet new -i PACKAGEID`, où `PACKAGEID` est identique au paramètre `<PackageId>` du fichier _.csproj_.</span><span class="sxs-lookup"><span data-stu-id="0af3f-156">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="0af3f-157">Cet ID de package est identique à l’identificateur du package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0af3f-157">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="0af3f-158">Désinstaller le pack de modèles</span><span class="sxs-lookup"><span data-stu-id="0af3f-158">Uninstall the template pack</span></span>

<span data-ttu-id="0af3f-159">Quelle que soit la façon dont vous avez installé le pack de modèles, directement avec le fichier _.nupkg_ ou avec le flux NuGet, la suppression d’un pack de modèles est identique.</span><span class="sxs-lookup"><span data-stu-id="0af3f-159">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="0af3f-160">Utilisez `<PackageId>` du modèle à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="0af3f-160">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="0af3f-161">Vous pouvez obtenir la liste des modèles installés en exécutant la commande `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="0af3f-161">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

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

<span data-ttu-id="0af3f-162">Exécutez `dotnet new -u AdatumCorporation.Utility.Templates` pour désinstaller le modèle.</span><span class="sxs-lookup"><span data-stu-id="0af3f-162">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="0af3f-163">La commande `dotnet new` génère des informations d’aide qui doivent omettre les modèles que vous avez installés précédemment.</span><span class="sxs-lookup"><span data-stu-id="0af3f-163">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="0af3f-164">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="0af3f-164">Congratulations!</span></span> <span data-ttu-id="0af3f-165">Vous avez installé et désinstallé un pack de modèles.</span><span class="sxs-lookup"><span data-stu-id="0af3f-165">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0af3f-166">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0af3f-166">Next steps</span></span>

<span data-ttu-id="0af3f-167">Pour en savoir plus sur les modèles, consultez l’article [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0af3f-167">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="0af3f-168">Wiki du dépôt GitHub dotnet/templating</span><span class="sxs-lookup"><span data-stu-id="0af3f-168">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="0af3f-169">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="0af3f-169">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="0af3f-170">Schéma *template.json* dans le magasin de schémas JSON</span><span class="sxs-lookup"><span data-stu-id="0af3f-170">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
