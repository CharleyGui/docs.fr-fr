---
title: Modèles personnalisés pour dotnet new
description: Découvrez les modèles personnalisés pour tout type de projet ou de fichier .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420879"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="5dbd7-103">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="5dbd7-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="5dbd7-104">Le [SDK .NET Core](https://dotnet.microsoft.com/download) est fourni avec de nombreux modèles déjà installés et prêts à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="5dbd7-105">La [ `dotnet new` commande](dotnet-new.md) n’est pas seulement le moyen d’utiliser un modèle, mais aussi la façon d’installer et de désinstaller les modèles.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="5dbd7-106">À compter de .NET Core 2.0, vous pouvez créer vos propres modèles personnalisés pour tout type de projet, tel qu’une application, un service, un outil ou une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="5dbd7-107">Vous pouvez même créer un modèle qui génère un ou plusieurs fichiers indépendants, comme un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="5dbd7-108">Vous pouvez installer des modèles personnalisés à partir d’un paquet NuGet sur n’importe quel flux NuGet, en faisant référence directement à un fichier NuGet *.nupkg,* ou en spécifiant un répertoire de système de fichiers qui contient le modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="5dbd7-109">Le moteur de modèle offre des fonctionnalités qui vous permettent de remplacer des valeurs, d’inclure et d’exclure des fichiers, ainsi que d’exécuter des opérations de traitement personnalisées quand votre modèle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="5dbd7-110">Le moteur de modèle est open source et le dépôt de code en ligne se trouve à l’adresse [dotnet/templating](https://github.com/dotnet/templating/) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="5dbd7-111">Visitez le dépôt [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) pour obtenir des exemples de modèles.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="5dbd7-112">Vous trouverez d’autres modèles, y compris des modèles tiers, à partir de la page [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (modèles disponibles pour dotnet new) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="5dbd7-113">Pour plus d’informations sur la création et l’utilisation de modèles personnalisés, consultez [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) et le [Wiki du dépôt GitHub dotnet/templating GitHub](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="5dbd7-114">Pour suivre une procédure pas à pas et créer un modèle, consultez le didacticiel [Créer un modèle personnalisé pour dotnet new](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="5dbd7-115">Modèles par défaut .NET</span><span class="sxs-lookup"><span data-stu-id="5dbd7-115">.NET default templates</span></span>

<span data-ttu-id="5dbd7-116">Quand vous installez le [SDK .NET Core](https://dotnet.microsoft.com/download), vous obtenez plus d’une dizaine de modèles intégrés pour la création de projets et de fichiers, notamment des applications de console, des bibliothèques de classes, des projets de test unitaire, des applications ASP.NET Core (dont les projets [Angular](https://angular.io/) et [React](https://facebook.github.io/react/)) et des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-116">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="5dbd7-117">Pour lister les modèles intégrés, exécutez la commande `dotnet new` avec l’option `-l|--list` :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="5dbd7-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="5dbd7-118">Configuration</span></span>

<span data-ttu-id="5dbd7-119">Un modèle est constitué des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="5dbd7-120">Dossiers et fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-120">Source files and folders.</span></span>
- <span data-ttu-id="5dbd7-121">Un fichier de configuration *(template.json*).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="5dbd7-122">Dossiers et fichiers sources</span><span class="sxs-lookup"><span data-stu-id="5dbd7-122">Source files and folders</span></span>

<span data-ttu-id="5dbd7-123">Les dossiers et fichiers sources incluent tous les fichiers et dossiers que le modèle doit utiliser quand la commande `dotnet new <TEMPLATE>` est exécutée.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="5dbd7-124">Le moteur de modèle est conçu pour utiliser des *projets exécutables* comme code source pour générer des projets.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="5dbd7-125">Cela a plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-125">This has several benefits:</span></span>

- <span data-ttu-id="5dbd7-126">Vous n’avez pas besoin d’injecter des jetons spéciaux dans le code source de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="5dbd7-127">Les fichiers de code ne sont pas des fichiers spéciaux ou des fichiers modifiés de quelque manière pour fonctionner avec le moteur de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="5dbd7-128">Ainsi, les outils que vous utilisez normalement avec des projets fonctionnent également avec le contenu du modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="5dbd7-129">Vous générez, exécutez et déboguez vos projets de modèle comme vous le feriez pour tout autre projet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="5dbd7-130">Vous pouvez rapidement créer un modèle à partir d’un projet existant en ajoutant simplement un fichier de configuration *./.template.config/template.json* au projet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="5dbd7-131">Les fichiers et dossiers stockés dans le modèle ne sont pas limités aux types de projet .NET formels.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="5dbd7-132">Les dossiers et fichiers sources peuvent comporter tout contenu que vous souhaitez créer quand vous utilisez le modèle, même si le moteur de modèle produit un seul fichier en guise de sortie.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="5dbd7-133">Les fichiers générés par le modèle peuvent être modifiés en fonction de la logique et des paramètres que vous avez fournis dans le fichier de configuration *template.json*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="5dbd7-134">L’utilisateur peut remplacer ces paramètres en passant des options à la commande `dotnet new <TEMPLATE>`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="5dbd7-135">Un exemple courant de logique personnalisée est la fourniture d’un nom pour une classe ou une variable dans le fichier de code qui est déployé par un modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="5dbd7-136">template.json</span><span class="sxs-lookup"><span data-stu-id="5dbd7-136">template.json</span></span>

<span data-ttu-id="5dbd7-137">Le fichier *template.json* est placé dans un dossier *.template.config* dans le répertoire racine du modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="5dbd7-138">Le fichier fournit des informations de configuration au moteur de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="5dbd7-139">La configuration minimale requiert les membres affichés dans le tableau suivant, qui suffisent pour créer un modèle fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="5dbd7-140">Membre</span><span class="sxs-lookup"><span data-stu-id="5dbd7-140">Member</span></span>            | <span data-ttu-id="5dbd7-141">Type</span><span class="sxs-lookup"><span data-stu-id="5dbd7-141">Type</span></span>          | <span data-ttu-id="5dbd7-142">Description</span><span class="sxs-lookup"><span data-stu-id="5dbd7-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="5dbd7-143">URI</span><span class="sxs-lookup"><span data-stu-id="5dbd7-143">URI</span></span>           | <span data-ttu-id="5dbd7-144">Schéma JSON pour le fichier *template.json*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="5dbd7-145">Les éditeurs qui prennent en charge les schémas JSON activent les fonctionnalités d’édition JSON quand le schéma est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="5dbd7-146">Par exemple, [Visual Studio Code](https://code.visualstudio.com/) exige ce membre pour activer IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="5dbd7-147">Utilisez la valeur de `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="5dbd7-148">string</span><span class="sxs-lookup"><span data-stu-id="5dbd7-148">string</span></span>        | <span data-ttu-id="5dbd7-149">Auteur du modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="5dbd7-150">tableau(chaîne)</span><span class="sxs-lookup"><span data-stu-id="5dbd7-150">array(string)</span></span> | <span data-ttu-id="5dbd7-151">Zéro ou plusieurs caractéristiques du modèle qu’un utilisateur peut utiliser pour rechercher le modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="5dbd7-152">Les classifications apparaissent également dans la colonne *Balises* quand il apparaît dans une liste de modèles produite à l’aide de la commande `dotnet new -l|--list`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="5dbd7-153">string</span><span class="sxs-lookup"><span data-stu-id="5dbd7-153">string</span></span>        | <span data-ttu-id="5dbd7-154">Nom unique pour ce modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="5dbd7-155">string</span><span class="sxs-lookup"><span data-stu-id="5dbd7-155">string</span></span>        | <span data-ttu-id="5dbd7-156">Nom de modèle que les utilisateurs doivent voir.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="5dbd7-157">string</span><span class="sxs-lookup"><span data-stu-id="5dbd7-157">string</span></span>        | <span data-ttu-id="5dbd7-158">Nom de raccourci par défaut pour sélectionner le modèle qui s’applique aux environnements où le nom du modèle est spécifié par l’utilisateur (non sélectionné par le biais d’une interface graphique utilisateur).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="5dbd7-159">Par exemple, le nom court est utile si les modèles sont utilisés à partir d’une invite de commandes avec des commandes CLI.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="5dbd7-160">Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="5dbd7-161">Pour plus d’informations sur le fichier *template.json*, consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="5dbd7-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="5dbd7-162"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5dbd7-162">Example</span></span>

<span data-ttu-id="5dbd7-163">Par exemple, voici un dossier de modèle qui contient deux fichiers de contenu : *console.cs* et *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="5dbd7-164">Notez que la présence du dossier requis nommé *.template.config*, qui contient le fichier *template.json*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="5dbd7-165">Le fichier *template.json* ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="5dbd7-166">Le dossier *mytemplate* est un pack de modèle installable.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="5dbd7-167">Une fois le pack installé, `shortName` peut être utilisé avec la commande `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="5dbd7-168">Par exemple, `dotnet new adatumconsole` devrait produire les fichiers `console.cs` et `readme.txt` dans le dossier actuel.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="5dbd7-169">Empaquetage d’un modèle dans un package NuGet (fichier nupkg)</span><span class="sxs-lookup"><span data-stu-id="5dbd7-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="5dbd7-170">Un modèle personnalisé est empaqueté avec la commande [dotnet pack](dotnet-pack.md) et un fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="5dbd7-171">Vous pouvez également utiliser [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) avec la commande [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) et un fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="5dbd7-172">Toutefois, NuGet nécessite .NET Framework sur Windows et [Mono](https://www.mono-project.com/) sur Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="5dbd7-173">Le fichier *.csproj* est légèrement différent d’un fichier de projet de code *.csproj* traditionnel.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="5dbd7-174">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-174">Note the following settings:</span></span>

01. <span data-ttu-id="5dbd7-175">Le paramètre `<PackageType>` est ajouté et défini sur `Template`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="5dbd7-176">Le paramètre `<PackageVersion>` est ajouté et défini sur un [numéro de version de NuGet](/nuget/reference/package-versioning) valide.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="5dbd7-177">Le paramètre `<PackageId>` est ajouté et la valeur est définie sur un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="5dbd7-178">Cet identificateur est utilisé pour désinstaller le pack de modèle et est utilisé par les flux NuGet pour inscrire votre pack de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="5dbd7-179">Les paramètres de métadonnées génériques doivent être définis : `<Title>`, `<Authors>`, `<Description>` et `<PackageTags>`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="5dbd7-180">Le paramètre `<TargetFramework>` doit être défini, même si le fichier binaire généré par le processus de modèle n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="5dbd7-181">Dans l’exemple ci-dessous, il est défini sur `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="5dbd7-182">Un pack de modèle, sous la forme d’un package NuGet *.nupkg*, requiert que tous les modèles soient stockés dans le dossier *content* du package.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="5dbd7-183">Il existe quelques paramètres supplémentaires à ajouter à un fichier *.csproj* pour vous assurer que le *.nupkg* généré peut être installé en tant que pack de modèle :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="5dbd7-184">Le paramètre `<IncludeContentInPack>` est défini sur `true` pour inclure n’importe quel fichier que le projet définit comme **contenu** dans le package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="5dbd7-185">Le paramètre `<IncludeBuildOutput>` est défini sur `false` pour exclure tous les fichiers binaires générés par le compilateur à partir du package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="5dbd7-186">Le paramètre `<ContentTargetFolders>` est défini sur `content`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="5dbd7-187">Cela permet de s’assurer que les fichiers définis comme **contenu** sont stockés dans le dossier *content* du package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="5dbd7-188">Ce dossier dans le package NuGet est analysé par le système de modèle dotnet.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="5dbd7-189">Un moyen simple d’empêcher tous les fichiers de code d’être compilés par votre projet de modèle est d’utiliser l’élément `<Compile Remove="**\*" />` dans votre fichier projet, dans un élément `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="5dbd7-190">Un moyen simple de structurer votre pack de modèle consiste à placer tous les modèles dans des dossiers individuels, puis chaque dossier de modèle à l’intérieur d’un dossier *templates* qui se trouve dans le même répertoire que votre fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="5dbd7-191">De cette façon, vous pouvez utiliser un élément de projet unique pour inclure tous les fichiers et dossiers dans les *modèles* en tant que **contenu**.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="5dbd7-192">À l’intérieur d’un élément `<ItemGroup>`, créez un élément `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="5dbd7-193">Voici un exemple de fichier *.csproj* respectant toutes les instructions ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="5dbd7-194">Il compresse le dossier enfant *templates* dans le dossier de package *content* et exclut tout fichier de code en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="5dbd7-195">L’exemple ci-dessous illustre la structure de fichiers et de dossiers lors de l’utilisation d’un *.csproj* pour créer un pack de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="5dbd7-196">Le fichier *MyDotnetTemplates.csproj* et le dossier *templates* se trouvent à la racine d’un répertoire nommé *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="5dbd7-197">Le dossier *templates* contient deux modèles, *mytemplate1* et *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="5dbd7-198">Chaque modèle a des fichiers de contenu et un dossier *.template.config* avec un fichier de configuration *template.json*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="5dbd7-199">Installation d’un modèle</span><span class="sxs-lookup"><span data-stu-id="5dbd7-199">Installing a template</span></span>

<span data-ttu-id="5dbd7-200">Utilisez la commande [dotnet new -i|--install](dotnet-new.md) pour installer un package.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="5dbd7-201">Pour installer un modèle à partir d’un package NuGet stocké sur nuget.org</span><span class="sxs-lookup"><span data-stu-id="5dbd7-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="5dbd7-202">Utilisez l’identificateur de package NuGet pour installer un package de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-202">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="5dbd7-203">Pour installer un modèle à partir d’un fichier nupkg local</span><span class="sxs-lookup"><span data-stu-id="5dbd7-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="5dbd7-204">Fournissez le chemin d’accès à un fichier de package NuGet *.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="5dbd7-205">Pour installer un modèle à partir d’un répertoire de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="5dbd7-205">To install a template from a file system directory</span></span>

<span data-ttu-id="5dbd7-206">Les modèles peuvent être installés à partir d’un dossier de modèles, comme le dossier *mytemplate1*, à partir de l’exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="5dbd7-207">Spécifiez le chemin du dossier *.template.config*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="5dbd7-208">Le chemin d’accès au répertoire du modèle n’a pas besoin d’être absolu.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="5dbd7-209">Toutefois, un chemin d’accès absolu est requis pour désinstaller un modèle qui est installé à partir d’un dossier.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="5dbd7-210">Obtenir la liste des modèles installés</span><span class="sxs-lookup"><span data-stu-id="5dbd7-210">Get a list of installed templates</span></span>

<span data-ttu-id="5dbd7-211">La commande de désinstallation, sans autres paramètres, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="5dbd7-212">Cette commande renvoie quelque chose de similaire à la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="5dbd7-213">Le premier niveau d’éléments après `Currently installed items:` est composé des identificateurs utilisés dans la désinstallation d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="5dbd7-214">Et dans l’exemple ci-dessus, `Microsoft.DotNet.Common.ItemTemplates` et `Microsoft.DotNet.Common.ProjectTemplates.3.0` sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="5dbd7-215">Si le modèle a été installé à l’aide d’un chemin d’accès du système de fichiers, cet identificateur est le chemin du dossier *.template.config*.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="5dbd7-216">Désinstallation d’un modèle</span><span class="sxs-lookup"><span data-stu-id="5dbd7-216">Uninstalling a template</span></span>

<span data-ttu-id="5dbd7-217">Utilisez la commande [dotnet new -u|--uninstall](dotnet-new.md) pour désinstaller un package.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="5dbd7-218">Si le package a été installé par un flux NuGet ou par un fichier *.nupkg* directement, fournissez l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="5dbd7-219">Si le package a été installé en spécifiant un chemin d’accès au dossier *.template.config*, utilisez ce chemin **absolu** pour désinstaller le package.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="5dbd7-220">Vous pouvez voir le chemin d’accès absolu du modèle dans la sortie fournie par la commande `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="5dbd7-221">Pour plus d’informations, consultez la section [Obtenir la liste des modèles installés](#get-a-list-of-installed-templates) ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="5dbd7-222">Créer un projet à l’aide d’un modèle personnalisé</span><span class="sxs-lookup"><span data-stu-id="5dbd7-222">Create a project using a custom template</span></span>

<span data-ttu-id="5dbd7-223">Une fois un modèle installé, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` comme vous le feriez avec tout autre modèle préinstallé.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="5dbd7-224">Vous pouvez également spécifier des [options](dotnet-new.md#options) dans la commande `dotnet new`, notamment des options de modèle que vous avez configurées dans les paramètres de modèle.</span><span class="sxs-lookup"><span data-stu-id="5dbd7-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="5dbd7-225">Indiquez le nom court du modèle directement dans la commande :</span><span class="sxs-lookup"><span data-stu-id="5dbd7-225">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="5dbd7-226">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dbd7-226">See also</span></span>

- [<span data-ttu-id="5dbd7-227">Créer un modèle personnalisé pour dotnet new (didacticiel)</span><span class="sxs-lookup"><span data-stu-id="5dbd7-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="5dbd7-228">Wiki du dépôt GitHub dotnet/templating</span><span class="sxs-lookup"><span data-stu-id="5dbd7-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="5dbd7-229">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="5dbd7-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="5dbd7-230">Guide pratique pour créer vos propres modèles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="5dbd7-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="5dbd7-231">Schéma *template.json* dans le magasin de schémas JSON</span><span class="sxs-lookup"><span data-stu-id="5dbd7-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
