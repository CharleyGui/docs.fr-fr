---
title: Créer un modèle d’élément pour la commande dotnet new - CLI .NET Core
description: Découvrez comment créer un modèle d’élément pour la commande dotnet new. Les modèles d’élément peuvent contenir n’importe quel nombre de fichiers.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503559"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="6603b-104">Didacticiel : créer un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="6603b-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="6603b-105">Avec .NET Core, vous pouvez créer et déployer des modèles qui génèrent des projets, des fichiers et même des ressources.</span><span class="sxs-lookup"><span data-stu-id="6603b-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="6603b-106">Ce tutoriel est le premier d’une série qui vous apprend comment créer, installer et désinstaller des modèles à utiliser avec la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="6603b-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="6603b-107">Dans cette partie de la série, vous découvrirez comment :</span><span class="sxs-lookup"><span data-stu-id="6603b-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="6603b-108">Créer une classe pour un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="6603b-108">Create a class for an item template</span></span>
> * <span data-ttu-id="6603b-109">Créer le dossier et le fichier de configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="6603b-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="6603b-110">Installer un modèle à partir d’un chemin de fichier</span><span class="sxs-lookup"><span data-stu-id="6603b-110">Install a template from a file path</span></span>
> * <span data-ttu-id="6603b-111">Tester un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="6603b-111">Test an item template</span></span>
> * <span data-ttu-id="6603b-112">Désinstaller un modèle d'élément</span><span class="sxs-lookup"><span data-stu-id="6603b-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6603b-113">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="6603b-113">Prerequisites</span></span>

* <span data-ttu-id="6603b-114">[SDK .NET Core 2.2](https://dotnet.microsoft.com/download) ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6603b-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="6603b-115">Lisez l’article de référence [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6603b-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="6603b-116">L’article de référence explique les notions de base sur les modèles et la façon dont ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="6603b-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="6603b-117">Certaines de ces informations seront répétées ici.</span><span class="sxs-lookup"><span data-stu-id="6603b-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="6603b-118">Ouvrez un terminal et accédez au dossier _working\templates_ .</span><span class="sxs-lookup"><span data-stu-id="6603b-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="6603b-119">Créer les dossiers requis</span><span class="sxs-lookup"><span data-stu-id="6603b-119">Create the required folders</span></span>

<span data-ttu-id="6603b-120">Cette série utilise un « dossier de travail » dans lequel se trouve votre source de modèle et un « dossier de test » utilisé pour tester vos modèles.</span><span class="sxs-lookup"><span data-stu-id="6603b-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="6603b-121">Le dossier de travail et le dossier de test doivent se trouver sous le même dossier parent.</span><span class="sxs-lookup"><span data-stu-id="6603b-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="6603b-122">Tout d’abord, créez le dossier parent, le nom n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="6603b-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="6603b-123">Puis, créez un sous-dossier nommé _working_.</span><span class="sxs-lookup"><span data-stu-id="6603b-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="6603b-124">Dans le dossier _working_, créez un sous-dossier nommé _templates_.</span><span class="sxs-lookup"><span data-stu-id="6603b-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="6603b-125">Ensuite, créez un dossier sous le dossier parent nommé _test_.</span><span class="sxs-lookup"><span data-stu-id="6603b-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="6603b-126">La structure des dossiers doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6603b-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="6603b-127">Créer un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="6603b-127">Create an item template</span></span>

<span data-ttu-id="6603b-128">Un modèle d’élément est un type spécifique de modèle qui contient un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="6603b-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="6603b-129">Ces types de modèles sont utiles lorsque vous souhaitez générer un fichier de configuration, de code ou de solution.</span><span class="sxs-lookup"><span data-stu-id="6603b-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="6603b-130">Dans cet exemple, vous allez créer une classe qui ajoute une méthode d’extension au type de chaîne.</span><span class="sxs-lookup"><span data-stu-id="6603b-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="6603b-131">Dans votre terminal, accédez au dossier _working\templates_ et créez un sous-dossier nommé _Extensions_.</span><span class="sxs-lookup"><span data-stu-id="6603b-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="6603b-132">Entrez dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="6603b-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="6603b-133">Créez un nouveau fichier nommé _CommonExtensions.cs_ et ouvrez-le avec votre éditeur de texte favori.</span><span class="sxs-lookup"><span data-stu-id="6603b-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="6603b-134">Cette classe fournit une méthode d’extension nommée `Reverse` qui inverse le contenu d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="6603b-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="6603b-135">Collez le code suivant et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="6603b-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="6603b-136">Maintenant que le contenu du modèle est créé, vous devez créer la configuration du modèle dans le dossier racine du modèle.</span><span class="sxs-lookup"><span data-stu-id="6603b-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="6603b-137">Créer la configuration du modèle</span><span class="sxs-lookup"><span data-stu-id="6603b-137">Create the template config</span></span>

<span data-ttu-id="6603b-138">Les modèles sont reconnus dans .NET Core par un dossier et un fichier de configuration spécifiques qui se trouvent à la racine de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="6603b-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="6603b-139">Dans ce didacticiel, votre dossier de modèles se trouve dans _working\templates\extensions_.</span><span class="sxs-lookup"><span data-stu-id="6603b-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="6603b-140">Lorsque vous créez un modèle, tous les fichiers et dossiers du dossier de modèle sont inclus dans le modèle, à l’exception du dossier de configuration spécial.</span><span class="sxs-lookup"><span data-stu-id="6603b-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="6603b-141">Ce dossier de configuration est nommé _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="6603b-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="6603b-142">Tout d’abord, créez un sous-dossier nommé _.template.config_ et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="6603b-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="6603b-143">Créez ensuite un nouveau fichier nommé _template.json_.</span><span class="sxs-lookup"><span data-stu-id="6603b-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="6603b-144">La structure des dossiers doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="6603b-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="6603b-145">Ouvrez le fichier _template. JSON_ avec votre éditeur de texte favori, puis collez le code JSON suivant et enregistrez-le.</span><span class="sxs-lookup"><span data-stu-id="6603b-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

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

<span data-ttu-id="6603b-146">Ce fichier de configuration contient tous les paramètres de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="6603b-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="6603b-147">Vous pouvez voir les paramètres de base, tels que `name` et `shortName`, mais il existe également une valeur `tags/type` qui est définie sur `item`.</span><span class="sxs-lookup"><span data-stu-id="6603b-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="6603b-148">Cela classe votre modèle en tant que modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="6603b-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="6603b-149">Il n’existe aucune restriction sur le type de modèle que vous créez.</span><span class="sxs-lookup"><span data-stu-id="6603b-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="6603b-150">Les valeurs `item` et `project` sont des noms courants que .NET Core recommande afin que les utilisateurs puissent facilement filtrer le type de modèle qu’ils recherchent.</span><span class="sxs-lookup"><span data-stu-id="6603b-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="6603b-151">L’élément `classifications` représente la colonne **tags** que vous voyez lorsque vous exécutez `dotnet new` et obtenez une liste de modèles.</span><span class="sxs-lookup"><span data-stu-id="6603b-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="6603b-152">Les utilisateurs peuvent également effectuer une recherche sur les balises de classification.</span><span class="sxs-lookup"><span data-stu-id="6603b-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="6603b-153">Ne confondez pas la propriété `tags` dans le fichier \*.json avec la liste de balises `classifications`.</span><span class="sxs-lookup"><span data-stu-id="6603b-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="6603b-154">Il s’agit de deux choses différentes, qui ont malheureusement le même nom.</span><span class="sxs-lookup"><span data-stu-id="6603b-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="6603b-155">Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="6603b-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="6603b-156">Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="6603b-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="6603b-157">Maintenant que vous avez un fichier _.template.config/template.json_ valide, votre modèle est prêt à être installé.</span><span class="sxs-lookup"><span data-stu-id="6603b-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="6603b-158">Dans votre terminal, accédez au dossier _extensions_ et exécutez la commande suivante pour installer le modèle situé dans le dossier actuel :</span><span class="sxs-lookup"><span data-stu-id="6603b-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="6603b-159">**Sous Windows** : `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="6603b-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="6603b-160">**Sous Linux ou macOS** : `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="6603b-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="6603b-161">Cette commande génère la liste des modèles installés, qui doivent inclure le vôtre.</span><span class="sxs-lookup"><span data-stu-id="6603b-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="6603b-162">Tester le modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="6603b-162">Test the item template</span></span>

<span data-ttu-id="6603b-163">Maintenant que vous avez un modèle d’élément installé, testez-le.</span><span class="sxs-lookup"><span data-stu-id="6603b-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="6603b-164">Accédez au dossier _test/_ et créez une application console avec `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="6603b-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="6603b-165">Cela génère un projet fonctionnel que vous pouvez facilement tester à l’aide de la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="6603b-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="6603b-166">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6603b-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="6603b-167">Exécutez le projet avec.</span><span class="sxs-lookup"><span data-stu-id="6603b-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="6603b-168">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="6603b-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="6603b-169">Ensuite, exécutez `dotnet new stringext` pour générer _CommonExtensions.cs_ à partir du modèle.</span><span class="sxs-lookup"><span data-stu-id="6603b-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="6603b-170">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="6603b-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="6603b-171">Modifiez le code dans _Program.cs_ pour inverser la chaîne `"Hello World"` avec la méthode d’extension fournie par le modèle.</span><span class="sxs-lookup"><span data-stu-id="6603b-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="6603b-172">Réexécutez le programme et vous verrez que le résultat est inversé.</span><span class="sxs-lookup"><span data-stu-id="6603b-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="6603b-173">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="6603b-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="6603b-174">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="6603b-174">Congratulations!</span></span> <span data-ttu-id="6603b-175">Vous avez créé et déployé un modèle d’élément avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6603b-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="6603b-176">Pour préparer la partie suivante de cette série de tutoriels, vous devez désinstaller le modèle que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="6603b-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="6603b-177">Veillez à supprimer également tous les fichiers du dossier _test_.</span><span class="sxs-lookup"><span data-stu-id="6603b-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="6603b-178">Vous revenez à un nouvel état prêt pour la section principale suivante de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="6603b-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="6603b-179">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="6603b-179">Uninstall the template</span></span>

<span data-ttu-id="6603b-180">Étant donné que vous avez installé le modèle par chemin de fichier, vous devez le désinstaller avec le chemin de fichier **absolu**.</span><span class="sxs-lookup"><span data-stu-id="6603b-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="6603b-181">Vous pouvez consulter la liste des modèles installés en exécutant la commande `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="6603b-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="6603b-182">Votre modèle doit être listé en dernier.</span><span class="sxs-lookup"><span data-stu-id="6603b-182">Your template should be listed last.</span></span> <span data-ttu-id="6603b-183">Utilisez le chemin indiqué pour désinstaller votre modèle à l’aide de la commande `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="6603b-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="6603b-184">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6603b-184">You get output similar to the following.</span></span>

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

<span data-ttu-id="6603b-185">Pour désinstaller un modèle, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="6603b-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="6603b-186">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6603b-186">Next steps</span></span>

<span data-ttu-id="6603b-187">Dans ce tutoriel, vous avez créé un modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="6603b-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="6603b-188">Pour savoir comment créer un modèle de projet, poursuivez cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="6603b-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6603b-189">Créer un modèle de projet</span><span class="sxs-lookup"><span data-stu-id="6603b-189">Create a project template</span></span>](cli-templates-create-project-template.md)
