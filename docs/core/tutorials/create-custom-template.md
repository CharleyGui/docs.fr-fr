---
title: Créer un modèle personnalisé pour dotnet new
description: Découvrez comment créer un modèle personnalisé pour la commande dotnet new dans ce didacticiel amusant.
author: mairaw
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: e47da048584ec31c275ff9c122d157f34556268a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299957"
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="8c118-103">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="8c118-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="8c118-104">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c118-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="8c118-105">Créer un modèle de base à partir d’un projet existant ou d’un nouveau projet d’application console</span><span class="sxs-lookup"><span data-stu-id="8c118-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="8c118-106">Empaqueter le modèle à des fins de distribution sur nuget.org ou à partir d’un fichier *nupkg* local</span><span class="sxs-lookup"><span data-stu-id="8c118-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="8c118-107">Installer le modèle à partir de nuget.org, d’un fichier *nupkg* local ou du système de fichiers local</span><span class="sxs-lookup"><span data-stu-id="8c118-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="8c118-108">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="8c118-108">Uninstall the template.</span></span>

<span data-ttu-id="8c118-109">Si vous préférez poursuivre le didacticiel avec un exemple complet, téléchargez [l’exemple de modèle de projet](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="8c118-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="8c118-110">L’exemple de modèle est configuré pour une distribution NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c118-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="8c118-111">Si vous souhaitez utiliser l’exemple téléchargé avec une distribution à partir du système de fichiers, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c118-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="8c118-112">Remontez le contenu du dossier *content* de l’exemple d’un niveau jusqu’au dossier *GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="8c118-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="8c118-113">Supprimez le dossier *content* vide.</span><span class="sxs-lookup"><span data-stu-id="8c118-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="8c118-114">Supprimez le fichier *nuspec*.</span><span class="sxs-lookup"><span data-stu-id="8c118-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c118-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8c118-115">Prerequisites</span></span>

- <span data-ttu-id="8c118-116">Installez le [SDK .NET Core 2.0](https://www.microsoft.com/net/core) ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="8c118-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="8c118-117">Lisez la rubrique de référence [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="8c118-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="8c118-118">Créer un modèle à partir d’un projet</span><span class="sxs-lookup"><span data-stu-id="8c118-118">Create a template from a project</span></span>

<span data-ttu-id="8c118-119">Utilisez un projet existant dont vous savez qu’il peut être compilé et exécuté, ou créez un projet d’application console dans un dossier de votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="8c118-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="8c118-120">Ce didacticiel suppose que le dossier de projet porte le nom *GarciaSoftware.ConsoleTemplate.CSharp* et qu’il est stocké à l’emplacement *Documents\Templates* dans le profil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c118-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="8c118-121">Le nom du modèle de projet du didacticiel est au format *\<nom de la société>.\<type de modèle>.\<langage de programmation>* , mais vous êtes libre de nommer votre projet et votre modèle comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8c118-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="8c118-122">Ajoutez un dossier nommé *.template.config* à la racine du projet.</span><span class="sxs-lookup"><span data-stu-id="8c118-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="8c118-123">Dans le dossier *.template.config*, créez un fichier *template.json* pour configurer votre modèle.</span><span class="sxs-lookup"><span data-stu-id="8c118-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="8c118-124">Pour obtenir plus d’informations et connaître les définitions de membre du fichier *template.json*, consultez la rubrique [Modèles personnalisés pour dotnet new](../tools/custom-templates.md#templatejson) et le schéma [*template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="8c118-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="8c118-125">Le modèle est terminé.</span><span class="sxs-lookup"><span data-stu-id="8c118-125">The template is finished.</span></span> <span data-ttu-id="8c118-126">À ce stade, vous avez deux options pour distribuer le modèle.</span><span class="sxs-lookup"><span data-stu-id="8c118-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="8c118-127">Pour continuer ce didacticiel, choisissez l’une des deux procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c118-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="8c118-128">[Distribution NuGet](#use-nuget-distribution) : installer le modèle à partir de NuGet ou du fichier local *nupkg*, et utiliser le modèle installé.</span><span class="sxs-lookup"><span data-stu-id="8c118-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="8c118-129">[Distribution à partir du système de fichiers](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="8c118-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="8c118-130">Utiliser la distribution NuGet</span><span class="sxs-lookup"><span data-stu-id="8c118-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="8c118-131">Empaqueter le modèle dans un package NuGet</span><span class="sxs-lookup"><span data-stu-id="8c118-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="8c118-132">Créez un dossier pour le package NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c118-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="8c118-133">Pour le didacticiel, le nom de dossier *GarciaSoftware.ConsoleTemplate.CSharp* est utilisé, et le dossier est créé dans un dossier *Documents\NuGetTemplates* du profil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c118-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="8c118-134">Créez un dossier nommé *content* dans le nouveau dossier de modèle pour y stocker les fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="8c118-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="8c118-135">Copiez le contenu du dossier de votre projet, avec son fichier *.template.config/template.json*, dans le dossier *content* que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="8c118-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="8c118-136">À côté du dossier *content*, ajoutez un fichier [*nuspec*](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="8c118-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="8c118-137">Le fichier nuspec est un fichier manifeste XML qui décrit le contenu d’un package et pilote le processus de création du package NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c118-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>

   ![Structure de répertoires représentant la disposition du package NuGet](./media/create-custom-template/nuget-directory-layout.png)

1. <span data-ttu-id="8c118-139">À l’intérieur d’un élément **\<packageTypes>** dans le fichier *nuspec*, ajoutez un élément **\<packageType>** avec une valeur d’attribut `name` de `Template`.</span><span class="sxs-lookup"><span data-stu-id="8c118-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="8c118-140">Le dossier *content* et le fichier *nuspec* doivent être tous les deux dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="8c118-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="8c118-141">Le tableau indique les éléments du fichier *nuspec* indispensables pour produire un modèle sous forme de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c118-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="8c118-142">Élément</span><span class="sxs-lookup"><span data-stu-id="8c118-142">Element</span></span>            | <span data-ttu-id="8c118-143">Type</span><span class="sxs-lookup"><span data-stu-id="8c118-143">Type</span></span>   | <span data-ttu-id="8c118-144">Description</span><span class="sxs-lookup"><span data-stu-id="8c118-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="8c118-145">**\<authors>**</span><span class="sxs-lookup"><span data-stu-id="8c118-145">**\<authors>**</span></span>     | <span data-ttu-id="8c118-146">string</span><span class="sxs-lookup"><span data-stu-id="8c118-146">string</span></span> | <span data-ttu-id="8c118-147">Liste séparée par des virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Les auteurs sont affichés dans la galerie NuGet sur nuget.org et servent à croiser les références des packages de mêmes auteurs.</span><span class="sxs-lookup"><span data-stu-id="8c118-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="8c118-148">**\<description>**</span><span class="sxs-lookup"><span data-stu-id="8c118-148">**\<description>**</span></span> | <span data-ttu-id="8c118-149">string</span><span class="sxs-lookup"><span data-stu-id="8c118-149">string</span></span> | <span data-ttu-id="8c118-150">Description longue du package pour l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c118-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="8c118-151">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="8c118-151">**\<id>**</span></span>          | <span data-ttu-id="8c118-152">string</span><span class="sxs-lookup"><span data-stu-id="8c118-152">string</span></span> | <span data-ttu-id="8c118-153">Identificateur de package respectant la casse, qui doit être unique dans nuget.org ou dans toute autre galerie susceptible de l’héberger.</span><span class="sxs-lookup"><span data-stu-id="8c118-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="8c118-154">Les ID ne peuvent pas contenir d’espaces ou de caractères qui ne sont pas valides pour une URL et suivent généralement les règles d’espace de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="8c118-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="8c118-155">Pour obtenir des conseils, consultez [Choix d’un identificateur de package unique et définition du numéro de version](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number).</span><span class="sxs-lookup"><span data-stu-id="8c118-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="8c118-156">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="8c118-156">**\<packageType>**</span></span> | <span data-ttu-id="8c118-157">string</span><span class="sxs-lookup"><span data-stu-id="8c118-157">string</span></span> | <span data-ttu-id="8c118-158">Placez cet élément à l’intérieur d’un élément **\<packageTypes>** parmi les éléments **\<metadata>** .</span><span class="sxs-lookup"><span data-stu-id="8c118-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="8c118-159">Affectez à l’attribut `name` de l’élément **\<packageType>** la valeur `Template`.</span><span class="sxs-lookup"><span data-stu-id="8c118-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="8c118-160">**\<version>**</span><span class="sxs-lookup"><span data-stu-id="8c118-160">**\<version>**</span></span>     | <span data-ttu-id="8c118-161">string</span><span class="sxs-lookup"><span data-stu-id="8c118-161">string</span></span> | <span data-ttu-id="8c118-162">Version du package, selon le format version_principale.version_secondaire.version_corrective.</span><span class="sxs-lookup"><span data-stu-id="8c118-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="8c118-163">Les numéros de version peuvent inclure un suffixe de préversion comme décrit dans [Préversions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="8c118-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="8c118-164">Consultez les [informations de référence sur .nuspec](/nuget/schema/nuspec) pour connaître le schéma du fichier *nuspec*.</span><span class="sxs-lookup"><span data-stu-id="8c118-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="8c118-165">Le fichier *nuspec* utilisé dans ce didacticiel est nommé *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* et présente le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="8c118-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="8c118-166">[Créez le package](/nuget/create-packages/creating-a-package#creating-the-package) à l’aide de la commande `nuget pack <PATH_TO_NUSPEC_FILE>`.</span><span class="sxs-lookup"><span data-stu-id="8c118-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="8c118-167">La commande suivante suppose que le dossier qui contient les composants NuGet se trouve à l’emplacement *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="8c118-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="8c118-168">Toutefois, où que vous placiez le dossier sur votre système, la commande `nuget pack` accepte le chemin du fichier *nuspec* :</span><span class="sxs-lookup"><span data-stu-id="8c118-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="8c118-169">Publication du package sur nuget.org</span><span class="sxs-lookup"><span data-stu-id="8c118-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="8c118-170">Pour publier un package NuGet, suivez les instructions de la rubrique [Créer et publier un package](/nuget/quickstart/create-and-publish-a-package#publish-the-package).</span><span class="sxs-lookup"><span data-stu-id="8c118-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="8c118-171">Cela dit, nous vous recommandons de ne pas publier le modèle du didacticiel sur NuGet, car une fois publié, il ne peut pas être supprimé, mais seulement retiré.</span><span class="sxs-lookup"><span data-stu-id="8c118-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="8c118-172">Le package NuGet se présentant désormais sous la forme d’un fichier *nupkg*, nous vous suggérons de suivre les instructions ci-dessous pour installer le modèle directement à partir du fichier *nupkg* local.</span><span class="sxs-lookup"><span data-stu-id="8c118-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="8c118-173">Installer le modèle à partir d’un package NuGet</span><span class="sxs-lookup"><span data-stu-id="8c118-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="8c118-174">Installer le modèle à partir du fichier *nupkg* local</span><span class="sxs-lookup"><span data-stu-id="8c118-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="8c118-175">Pour installer le modèle à partir du fichier *nupkg* que vous avez créé, utilisez la commande `dotnet new` avec l’option `-i|--install` et indiquez le chemin du fichier *nupkg* :</span><span class="sxs-lookup"><span data-stu-id="8c118-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="8c118-176">Installer le modèle à partir d’un package NuGet stocké sur nuget.org</span><span class="sxs-lookup"><span data-stu-id="8c118-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="8c118-177">Si vous souhaitez installer un modèle à partir d’un package NuGet stocké sur nuget.org, utilisez la commande `dotnet new` avec l’option `-i|--install` et indiquez le nom du package NuGet :</span><span class="sxs-lookup"><span data-stu-id="8c118-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="8c118-178">L’exemple est fourni à des fins de démonstration uniquement.</span><span class="sxs-lookup"><span data-stu-id="8c118-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="8c118-179">Aucun package NuGet `GarciaSoftware.ConsoleTemplate.CSharp` n’existe sur nuget.org, et nous vous déconseillons de publier et de consommer des modèles de test à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c118-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="8c118-180">Si vous exécutez la commande, aucun modèle n’est installé.</span><span class="sxs-lookup"><span data-stu-id="8c118-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="8c118-181">Toutefois, vous pouvez installer un modèle qui n’a pas été publié sur nuget.org en référençant le fichier *nupkg* directement sur votre système de fichiers local, comme indiqué dans la section précédente [Installer le modèle à partir du fichier nupkg local](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="8c118-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="8c118-182">Si vous souhaitez un exemple concret d’installation d’un modèle à partir d’un package sur nuget.org, vous pouvez utiliser le [modèle NUnit 3 pour dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="8c118-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="8c118-183">Ce modèle définit un projet pour utiliser des tests unitaires NUnit.</span><span class="sxs-lookup"><span data-stu-id="8c118-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="8c118-184">Utilisez la commande suivante pour l’installer :</span><span class="sxs-lookup"><span data-stu-id="8c118-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="8c118-185">Quand vous affichez la liste des modèles avec `dotnet new -l`, le *projet de test NUnit 3* apparaît sous la forme abrégée *nunit*.</span><span class="sxs-lookup"><span data-stu-id="8c118-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="8c118-186">Vous êtes prêt à utiliser le modèle dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="8c118-186">You're ready to use the template in the next section.</span></span>

![Fenêtre de console montrant le modèle NUnit avec d’autres modèles](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="8c118-188">Créer un projet à partir du modèle</span><span class="sxs-lookup"><span data-stu-id="8c118-188">Create a project from the template</span></span>

<span data-ttu-id="8c118-189">Une fois le modèle installé à partir de NuGet, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` à partir du répertoire où vous souhaitez que soit placée la sortie du moteur de modèle (sauf si vous utilisez l’option `-o|--output` pour spécifier un répertoire spécifique).</span><span class="sxs-lookup"><span data-stu-id="8c118-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="8c118-190">Pour plus d’informations, consultez [Options `dotnet new`](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="8c118-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="8c118-191">Indiquez le nom court du modèle directement dans la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="8c118-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="8c118-192">Pour créer un projet à partir du modèle NUnit, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8c118-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="8c118-193">La console indique que le projet est créé et que les packages du projet sont restaurés.</span><span class="sxs-lookup"><span data-stu-id="8c118-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="8c118-194">Une fois la commande exécutée, le projet est prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="8c118-194">After the command is run, the project is ready for use.</span></span>

![La fenêtre de console affiche la sortie du nouveau nunit dotnet incluant la restauration des dépendances du projet](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="8c118-196">Pour désinstaller un modèle à partir d’un package NuGet stocké sur nuget.org</span><span class="sxs-lookup"><span data-stu-id="8c118-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="8c118-197">L’exemple est fourni à des fins de démonstration uniquement.</span><span class="sxs-lookup"><span data-stu-id="8c118-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="8c118-198">Aucun package NuGet `GarciaSoftware.ConsoleTemplate.CSharp` n’existe sur nuget.org ou n’est installé avec le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c118-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="8c118-199">Si vous exécutez la commande, aucun modèle/package n’est désinstallé et vous recevez l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="8c118-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
>
> > <span data-ttu-id="8c118-200">Impossible de désinstaller quelque chose appelé 'GarciaSoftware.ConsoleTemplate.CSharp'.</span><span class="sxs-lookup"><span data-stu-id="8c118-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="8c118-201">Si vous avez installé le [modèle NUnit 3 pour dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) et que vous souhaitez le désinstaller, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8c118-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="8c118-202">Désinstaller le modèle à partir d’un fichier nupkg local</span><span class="sxs-lookup"><span data-stu-id="8c118-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="8c118-203">Quand vous souhaitez désinstaller le modèle, n’essayez pas d’utiliser le chemin du fichier *nupkg*.</span><span class="sxs-lookup"><span data-stu-id="8c118-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="8c118-204">*La tentative de désinstaller un modèle à l’aide de `dotnet new -u <PATH_TO_NUPKG_FILE>` est vouée à l’échec.*</span><span class="sxs-lookup"><span data-stu-id="8c118-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="8c118-205">Référencez le package par son `id` :</span><span class="sxs-lookup"><span data-stu-id="8c118-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="8c118-206">Utiliser la distribution à partir du système de fichiers</span><span class="sxs-lookup"><span data-stu-id="8c118-206">Use file system distribution</span></span>

<span data-ttu-id="8c118-207">Pour distribuer le modèle, placez le dossier du modèle de projet dans un emplacement accessible aux utilisateurs de votre réseau.</span><span class="sxs-lookup"><span data-stu-id="8c118-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="8c118-208">Utilisez la commande `dotnet new` avec l’option `-i|--install` et spécifiez le chemin du dossier de modèles (le dossier de projet contenant le projet et le dossier *.template.config*).</span><span class="sxs-lookup"><span data-stu-id="8c118-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="8c118-209">Ce didacticiel suppose que le modèle de projet est stocké dans le dossier *Documents/Templates* du profil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c118-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="8c118-210">À partir de cet emplacement, installez le modèle à l’aide de la commande suivante en remplaçant \<USER> par le nom de profil de l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="8c118-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="8c118-211">Créer un projet à partir du modèle</span><span class="sxs-lookup"><span data-stu-id="8c118-211">Create a project from the template</span></span>

<span data-ttu-id="8c118-212">Une fois le modèle installé à partir du système de fichiers, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` à partir du répertoire où vous souhaitez que soit placée la sortie du moteur de modèle (sauf si vous utilisez l’option `-o|--output` pour spécifier un répertoire spécifique).</span><span class="sxs-lookup"><span data-stu-id="8c118-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="8c118-213">Pour plus d’informations, consultez [Options `dotnet new`](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="8c118-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="8c118-214">Indiquez le nom court du modèle directement dans la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="8c118-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="8c118-215">À partir d’un nouveau dossier de projet créé à l’emplacement *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, créez un projet à partir du modèle `garciaconsole` :</span><span class="sxs-lookup"><span data-stu-id="8c118-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="8c118-216">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="8c118-216">Uninstall the template</span></span>

<span data-ttu-id="8c118-217">Si vous avez créé le modèle sur votre système de fichiers local à l’emplacement *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, désinstallez-le à l’aide du commutateur `-u|--uninstall` et du chemin du dossier de modèles :</span><span class="sxs-lookup"><span data-stu-id="8c118-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="8c118-218">Pour désinstaller le modèle de votre système de fichiers local, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="8c118-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="8c118-219">Par exemple, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="8c118-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8c118-220">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="8c118-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c118-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c118-221">See also</span></span>

- [<span data-ttu-id="8c118-222">Wiki du dépôt GitHub dotnet/templating</span><span class="sxs-lookup"><span data-stu-id="8c118-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="8c118-223">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="8c118-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="8c118-224">Guide pratique pour créer vos propres modèles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="8c118-224">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="8c118-225">Schéma *template.json* dans le magasin de schémas JSON</span><span class="sxs-lookup"><span data-stu-id="8c118-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
