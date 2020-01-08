---
title: Créer un modèle de projet pour dotnet new
description: Découvrez comment créer un modèle de projet pour la commande dotnet new.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 64b029f87135c3424d01a6833619f0aec3833883
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340367"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="4ecdf-103">Didacticiel : créer un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="4ecdf-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="4ecdf-104">Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="4ecdf-105">Ce tutoriel est le deuxième d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="4ecdf-106">Dans cette partie de la série, vous découvrirez comment :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4ecdf-107">Créer les ressources d’un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="4ecdf-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="4ecdf-108">Créer le dossier et le fichier de configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="4ecdf-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="4ecdf-109">Installer un modèle à partir d’un chemin de fichier</span><span class="sxs-lookup"><span data-stu-id="4ecdf-109">Install a template from a file path</span></span>
> * <span data-ttu-id="4ecdf-110">Tester un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="4ecdf-110">Test an item template</span></span>
> * <span data-ttu-id="4ecdf-111">Désinstaller un modèle d'élément</span><span class="sxs-lookup"><span data-stu-id="4ecdf-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ecdf-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ecdf-112">Prerequisites</span></span>

* <span data-ttu-id="4ecdf-113">Complétez la [première partie](cli-templates-create-item-template.md) de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="4ecdf-114">Ouvrez un terminal et accédez au dossier _working\templates_ .</span><span class="sxs-lookup"><span data-stu-id="4ecdf-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="4ecdf-115">Créer un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="4ecdf-115">Create a project template</span></span>

<span data-ttu-id="4ecdf-116">Les modèles de projet produisent des projets prêts à être exécutés, qui permettent aux utilisateurs de démarrer facilement avec un jeu de code fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="4ecdf-117">.NET Core comprend quelques modèles de projet, tels qu’une application console ou une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="4ecdf-118">Dans cet exemple, vous allez créer un nouveau projet console qui active C# 8.0 et génère un point d’entrée `async main`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="4ecdf-119">Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="4ecdf-120">Entrez dans le sous-dossier et exécutez `dotnet new console` pour générer l’application console standard.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="4ecdf-121">Vous allez modifier les fichiers générés par ce modèle pour créer un nouveau modèle.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="4ecdf-122">Modifier Program.cs</span><span class="sxs-lookup"><span data-stu-id="4ecdf-122">Modify Program.cs</span></span>

<span data-ttu-id="4ecdf-123">Ouvrez le fichier _program.cs_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="4ecdf-124">Le projet console n’utilise pas de point d’entrée asynchrone, nous allons donc l’ajouter.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="4ecdf-125">Modifiez votre code comme suit et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-125">Change your code to the following and save the file:</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="4ecdf-126">Modifier consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="4ecdf-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="4ecdf-127">Nous allons mettre à jour vers la version 8.0 la version de langage C# que le projet utilise.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="4ecdf-128">Modifiez le fichier _consoleasync.csproj_ et ajoutez le paramètre `<LangVersion>` à un nœud `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="4ecdf-129">Générer le projet</span><span class="sxs-lookup"><span data-stu-id="4ecdf-129">Build the project</span></span>

<span data-ttu-id="4ecdf-130">Avant de terminer un modèle de projet, vous devez le tester pour vous assurer qu’il se compile et s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="4ecdf-131">Dans votre terminal, exécutez la commande `dotnet run`. La sortie suivante doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="4ecdf-132">Vous pouvez supprimer les dossiers _obj_ et _bin_ créés à l’aide de `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="4ecdf-133">La suppression de ces fichiers garantit que votre modèle inclue uniquement les fichiers associés à votre modèle et pas les fichiers qui résultent d’une action de génération.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="4ecdf-134">Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="4ecdf-135">Créer la configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="4ecdf-135">Create the template config</span></span>

<span data-ttu-id="4ecdf-136">Les modèles sont reconnus dans .NET Core par un dossier et un fichier de configuration spécifiques qui se trouvent à la racine de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="4ecdf-137">Dans ce didacticiel, votre dossier de modèles se trouve dans _working\templates\consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-137">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="4ecdf-138">Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="4ecdf-139">Ce dossier de configuration est nommé _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="4ecdf-140">Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="4ecdf-141">Créez ensuite un nouveau fichier nommé _template.json_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="4ecdf-142">La structure des dossiers doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="4ecdf-143">Ouvrez le fichier _template.json_ avec votre éditeur de texte favori, puis collez le code json suivant et enregistrez-le :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

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

<span data-ttu-id="4ecdf-144">Ce fichier de configuration contient tous les paramètres de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="4ecdf-145">Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `project`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="4ecdf-146">Cela désigne votre modèle en tant que modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-146">This designates your template as a project template.</span></span> <span data-ttu-id="4ecdf-147">Il n’existe aucune restriction sur le type de modèle que vous créez.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="4ecdf-148">Les valeurs `item` et `project` sont des noms courants que .NET Core recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="4ecdf-149">L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="4ecdf-150">Les utilisateurs peuvent également effectuer une recherche sur les balises de classification.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="4ecdf-151">Ne confondez pas la propriété `tags` dans le fichier json avec la liste de balises `classifications`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="4ecdf-152">Il s’agit de deux choses différentes, qui ont malheureusement le même nom.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="4ecdf-153">Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="4ecdf-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="4ecdf-154">Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="4ecdf-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="4ecdf-155">Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="4ecdf-156">Avant d’installer le modèle, veillez à supprimer tous les fichiers et dossiers supplémentaires que vous ne souhaitez pas inclure dans votre modèle, comme les dossiers _bin_ ou _obj_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="4ecdf-157">Dans votre terminal, accédez au dossier _consoleasync_ et exécutez `dotnet new -i .\` pour installer le modèle situé dans le dossier actuel.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="4ecdf-158">Si vous utilisez un système d’exploitation Linux ou MacOS, utilisez une barre oblique : `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="4ecdf-159">Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-159">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\consoleasync> dotnet new -i .\
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

### <a name="test-the-project-template"></a><span data-ttu-id="4ecdf-160">Tester le modèle de projet</span><span class="sxs-lookup"><span data-stu-id="4ecdf-160">Test the project template</span></span>

<span data-ttu-id="4ecdf-161">Maintenant que vous avez un modèle d’élément installé, testez-le.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="4ecdf-162">Accédez au dossier _test_ et créez une application console avec `dotnet new consoleasync`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-162">Navigate to the _test_ folder and create a new console application with `dotnet new consoleasync`.</span></span> <span data-ttu-id="4ecdf-163">Cela génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="4ecdf-164">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="4ecdf-164">Congratulations!</span></span> <span data-ttu-id="4ecdf-165">Vous avez créé et déployé un modèle de projet avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="4ecdf-166">Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="4ecdf-167">Veillez à supprimer également tous les fichiers du dossier _test_.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="4ecdf-168">Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="4ecdf-169">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="4ecdf-169">Uninstall the template</span></span>

<span data-ttu-id="4ecdf-170">Étant donné que vous avez installé le modèle avec un chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="4ecdf-171">Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="4ecdf-172">Votre modèle doit être listé en dernier.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-172">Your template should be listed last.</span></span> <span data-ttu-id="4ecdf-173">Utilisez le chemin indiqué pour désinstaller votre modèle à l’aide de la commande `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```console
C:\working> dotnet new -u
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

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="4ecdf-174">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ecdf-174">Next steps</span></span>

<span data-ttu-id="4ecdf-175">Dans ce tutoriel, vous avez créé un modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="4ecdf-176">Pour savoir comment empaqueter les modèles d’élément et de projet dans un fichier facile à utiliser, poursuivez cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="4ecdf-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ecdf-177">Créer un pack de modèles</span><span class="sxs-lookup"><span data-stu-id="4ecdf-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
