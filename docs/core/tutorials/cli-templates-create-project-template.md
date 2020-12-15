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
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="9787a-103">Didacticiel : créer un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="9787a-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="9787a-104">Avec .NET, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources.</span><span class="sxs-lookup"><span data-stu-id="9787a-104">With .NET, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="9787a-105">Ce tutoriel est le deuxième d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="9787a-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="9787a-106">Dans cette partie de la série, vous découvrirez comment :</span><span class="sxs-lookup"><span data-stu-id="9787a-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9787a-107">Créer les ressources d’un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="9787a-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="9787a-108">Créer le dossier et le fichier de configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="9787a-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="9787a-109">Installer un modèle à partir d’un chemin de fichier</span><span class="sxs-lookup"><span data-stu-id="9787a-109">Install a template from a file path</span></span>
> * <span data-ttu-id="9787a-110">Tester un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="9787a-110">Test an item template</span></span>
> * <span data-ttu-id="9787a-111">Désinstaller un modèle d'élément</span><span class="sxs-lookup"><span data-stu-id="9787a-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9787a-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="9787a-112">Prerequisites</span></span>

* <span data-ttu-id="9787a-113">Complétez la [première partie](cli-templates-create-item-template.md) de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="9787a-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="9787a-114">Ouvrez un terminal et accédez au dossier _working\templates_.</span><span class="sxs-lookup"><span data-stu-id="9787a-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="9787a-115">Créer un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="9787a-115">Create a project template</span></span>

<span data-ttu-id="9787a-116">Les modèles de projet produisent des projets prêts à être exécutés, qui permettent aux utilisateurs de démarrer facilement avec un jeu de code fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="9787a-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="9787a-117">.NET comprend quelques modèles de projet, tels qu’une application console ou une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="9787a-117">.NET includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="9787a-118">Dans cet exemple, vous allez créer un nouveau projet de console qui active C# 9,0 et génère un `async main` point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9787a-118">In this example, you'll create a new console project that enables C# 9.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="9787a-119">Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="9787a-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="9787a-120">Entrez dans le sous-dossier et exécutez `dotnet new console` pour générer l’application console standard.</span><span class="sxs-lookup"><span data-stu-id="9787a-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="9787a-121">Vous allez modifier les fichiers générés par ce modèle pour créer un nouveau modèle.</span><span class="sxs-lookup"><span data-stu-id="9787a-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="9787a-122">Modifier Program.cs</span><span class="sxs-lookup"><span data-stu-id="9787a-122">Modify Program.cs</span></span>

<span data-ttu-id="9787a-123">Ouvrez le fichier _program.cs_.</span><span class="sxs-lookup"><span data-stu-id="9787a-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="9787a-124">Le projet console n’utilise pas de point d’entrée asynchrone, nous allons donc l’ajouter.</span><span class="sxs-lookup"><span data-stu-id="9787a-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="9787a-125">Remplacez votre code par ce qui suit et enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="9787a-125">Change your code to the following and save the file.</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="9787a-126">Modifier consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="9787a-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="9787a-127">Nous allons mettre à jour la version du langage C# que le projet utilise pour la version 9,0.</span><span class="sxs-lookup"><span data-stu-id="9787a-127">Let's update the C# language version the project uses to version 9.0.</span></span> <span data-ttu-id="9787a-128">Modifiez le fichier _consoleasync.csproj_ et ajoutez le paramètre `<LangVersion>` à un nœud `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="9787a-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>

    <LangVersion>9.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="9787a-129">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="9787a-129">Build the project</span></span>

<span data-ttu-id="9787a-130">Avant de terminer un modèle de projet, vous devez le tester pour vous assurer qu’il se compile et s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="9787a-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="9787a-131">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="9787a-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="9787a-132">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="9787a-132">You get the following output.</span></span>

```console
Hello World with C# 9.0!
```

<span data-ttu-id="9787a-133">Vous pouvez supprimer les dossiers _obj_ et _bin_ créés à l’aide de `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="9787a-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="9787a-134">La suppression de ces fichiers garantit que votre modèle comprend uniquement les fichiers associés à votre modèle, et non les fichiers qui résultent d’une action de génération.</span><span class="sxs-lookup"><span data-stu-id="9787a-134">Deleting these files ensures your template only includes the files related to your template and not any files that result from a build action.</span></span>

<span data-ttu-id="9787a-135">Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.</span><span class="sxs-lookup"><span data-stu-id="9787a-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="9787a-136">Créer la configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="9787a-136">Create the template config</span></span>

<span data-ttu-id="9787a-137">Les modèles sont reconnus dans .NET par un dossier spécial et un fichier de configuration qui se trouvent à la racine de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="9787a-137">Templates are recognized in .NET by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="9787a-138">Dans ce tutoriel, votre dossier de modèle se trouve dans _working\templates\consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="9787a-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="9787a-139">Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial.</span><span class="sxs-lookup"><span data-stu-id="9787a-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="9787a-140">Ce dossier de configuration est nommé _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="9787a-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="9787a-141">Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="9787a-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="9787a-142">Créez ensuite un nouveau fichier nommé _template.json_.</span><span class="sxs-lookup"><span data-stu-id="9787a-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="9787a-143">Votre structure de dossiers doit ressembler à ceci.</span><span class="sxs-lookup"><span data-stu-id="9787a-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="9787a-144">Ouvrez le _template.jsdans_ avec votre éditeur de texte préféré et collez le code JSON suivant et enregistrez-le.</span><span class="sxs-lookup"><span data-stu-id="9787a-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

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

<span data-ttu-id="9787a-145">Ce fichier de configuration contient tous les paramètres de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="9787a-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="9787a-146">Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `project`.</span><span class="sxs-lookup"><span data-stu-id="9787a-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="9787a-147">Cela désigne votre modèle en tant que modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="9787a-147">This designates your template as a project template.</span></span> <span data-ttu-id="9787a-148">Il n’existe aucune restriction sur le type de modèle que vous créez.</span><span class="sxs-lookup"><span data-stu-id="9787a-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="9787a-149">Les `item` `project` valeurs et sont des noms communs que .net recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.</span><span class="sxs-lookup"><span data-stu-id="9787a-149">The `item` and `project` values are common names that .NET recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="9787a-150">L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles.</span><span class="sxs-lookup"><span data-stu-id="9787a-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="9787a-151">Les utilisateurs peuvent également effectuer une recherche sur les balises de classification.</span><span class="sxs-lookup"><span data-stu-id="9787a-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="9787a-152">Ne confondez pas la propriété `tags` dans le fichier json avec la liste de balises `classifications`.</span><span class="sxs-lookup"><span data-stu-id="9787a-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="9787a-153">Il s’agit de deux choses différentes, qui ont malheureusement le même nom.</span><span class="sxs-lookup"><span data-stu-id="9787a-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="9787a-154">Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="9787a-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="9787a-155">Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="9787a-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="9787a-156">Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé.</span><span class="sxs-lookup"><span data-stu-id="9787a-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="9787a-157">Avant d’installer le modèle, veillez à supprimer tous les fichiers et dossiers supplémentaires que vous ne souhaitez pas inclure dans votre modèle, comme les dossiers _bin_ ou _obj_.</span><span class="sxs-lookup"><span data-stu-id="9787a-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="9787a-158">Dans votre terminal, accédez au dossier _consoleasync_ et exécutez `dotnet new -i .\` pour installer le modèle situé dans le dossier actuel.</span><span class="sxs-lookup"><span data-stu-id="9787a-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="9787a-159">Si vous utilisez un système d’exploitation Linux ou macOS, utilisez une barre oblique : `dotnet new -i ./` .</span><span class="sxs-lookup"><span data-stu-id="9787a-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="9787a-160">Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.</span><span class="sxs-lookup"><span data-stu-id="9787a-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="9787a-161">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="9787a-161">You get output similar to the following.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="9787a-162">Tester le modèle de projet</span><span class="sxs-lookup"><span data-stu-id="9787a-162">Test the project template</span></span>

<span data-ttu-id="9787a-163">Maintenant que vous avez un modèle de projet installé, testez-le.</span><span class="sxs-lookup"><span data-stu-id="9787a-163">Now that you have a project template installed, test it.</span></span>

1. <span data-ttu-id="9787a-164">Accéder au dossier de _test_</span><span class="sxs-lookup"><span data-stu-id="9787a-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="9787a-165">Créez une application console à l’aide de la commande suivante, qui génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la `dotnet run` commande.</span><span class="sxs-lookup"><span data-stu-id="9787a-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="9787a-166">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="9787a-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="9787a-167">Exécutez le projet à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="9787a-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="9787a-168">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="9787a-168">You get the following output.</span></span>

    ```console
    Hello World with C# 9.0!
    ```

<span data-ttu-id="9787a-169">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="9787a-169">Congratulations!</span></span> <span data-ttu-id="9787a-170">Vous avez créé et déployé un modèle de projet avec .NET.</span><span class="sxs-lookup"><span data-stu-id="9787a-170">You created and deployed a project template with .NET.</span></span> <span data-ttu-id="9787a-171">Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="9787a-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="9787a-172">Veillez à supprimer également tous les fichiers du dossier _test_.</span><span class="sxs-lookup"><span data-stu-id="9787a-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="9787a-173">Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="9787a-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="9787a-174">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="9787a-174">Uninstall the template</span></span>

<span data-ttu-id="9787a-175">Étant donné que vous avez installé le modèle avec un chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**.</span><span class="sxs-lookup"><span data-stu-id="9787a-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="9787a-176">Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="9787a-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="9787a-177">Votre modèle doit être listé en dernier.</span><span class="sxs-lookup"><span data-stu-id="9787a-177">Your template should be listed last.</span></span> <span data-ttu-id="9787a-178">Utilisez la `Uninstall Command` liste pour désinstaller votre modèle.</span><span class="sxs-lookup"><span data-stu-id="9787a-178">Use the `Uninstall Command` listed to uninstall your template.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="9787a-179">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="9787a-179">You get output similar to the following.</span></span>

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

<span data-ttu-id="9787a-180">Pour désinstaller le modèle que vous avez créé, exécutez le `Uninstall Command` qui est affiché dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="9787a-180">To uninstall the template that you created, run the `Uninstall Command` that is shown in the output.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="9787a-181">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9787a-181">Next steps</span></span>

<span data-ttu-id="9787a-182">Dans ce tutoriel, vous avez créé un modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="9787a-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="9787a-183">Pour savoir comment empaqueter les modèles d’élément et de projet dans un fichier facile à utiliser, poursuivez cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="9787a-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9787a-184">Créer un pack de modèles</span><span class="sxs-lookup"><span data-stu-id="9787a-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
