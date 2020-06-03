---
title: Commande dotnet list package
description: La commande 'dotnet list package' est pratique pour lister les références de packages à un projet ou à une solution.
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463664"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="4245d-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="4245d-103">dotnet list package</span></span>

<span data-ttu-id="4245d-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,2 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4245d-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4245d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="4245d-105">Name</span></span>

<span data-ttu-id="4245d-106">`dotnet list package` - Liste toutes les références de package d’un projet ou d’une solution.</span><span class="sxs-lookup"><span data-stu-id="4245d-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4245d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4245d-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="4245d-108">Description</span><span class="sxs-lookup"><span data-stu-id="4245d-108">Description</span></span>

<span data-ttu-id="4245d-109">La commande `dotnet list package` est pratique pour lister toutes les références de packages NuGet à un projet ou à une solution spécifique.</span><span class="sxs-lookup"><span data-stu-id="4245d-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="4245d-110">Vous devez d’abord générer le projet afin d’obtenir les ressources nécessaires au traitement de cette commande.</span><span class="sxs-lookup"><span data-stu-id="4245d-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="4245d-111">L’exemple suivant montre le résultat de la commande `dotnet list package` pour le projet [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="4245d-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="4245d-112">La colonne **Demandée** fait référence à la version du package spécifiée dans le fichier projet et peut représenter une plage.</span><span class="sxs-lookup"><span data-stu-id="4245d-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="4245d-113">La colonne **Résolue** répertorie la version utilisée par le projet aide et représente toujours une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="4245d-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="4245d-114">Les packages affichant une lettre `(A)` en regard de leurs noms représentent des [références de package implicites](csproj.md#implicit-package-references) déduites de vos paramètres de projet (type `Sdk`, propriété `<TargetFramework>` ou `<TargetFrameworks>`, etc.)</span><span class="sxs-lookup"><span data-stu-id="4245d-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="4245d-115">Utilisez l’option `--outdated` pour savoir s’il existe des versions plus récentes des packages que vous utilisez dans vos projets.</span><span class="sxs-lookup"><span data-stu-id="4245d-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="4245d-116">Par défaut, `--outdated` répertorie les derniers packages stables, sauf si la version résolue est également une version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="4245d-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="4245d-117">Pour inclure des versions préliminaires lors de l’énumération des versions plus récentes, spécifiez également l’option `--include-prerelease`.</span><span class="sxs-lookup"><span data-stu-id="4245d-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="4245d-118">Les exemples suivants montrent le résultat de la commande `dotnet list package --outdated --include-prerelease` pour le même projet que l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="4245d-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="4245d-119">Si vous avez besoin de savoir si votre projet comporte des dépendances transitives, utilisez l’option `--include-transitive`.</span><span class="sxs-lookup"><span data-stu-id="4245d-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="4245d-120">Les dépendances transitives se produisent lorsque vous ajoutez un package à votre projet, qui à son tour s’appuie sur un autre package.</span><span class="sxs-lookup"><span data-stu-id="4245d-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="4245d-121">L’exemple suivant montre le résultat de l’exécution de la commande `dotnet list package --include-transitive` pour le projet [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin), qui affiche les packages de niveau supérieur et ceux dont ils dépendent :</span><span class="sxs-lookup"><span data-stu-id="4245d-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="4245d-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="4245d-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="4245d-123">Le fichier projet ou solution à traiter.</span><span class="sxs-lookup"><span data-stu-id="4245d-123">The project or solution file to operate on.</span></span> <span data-ttu-id="4245d-124">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="4245d-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="4245d-125">Si la commande trouve plusieurs solutions ou projets, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="4245d-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="4245d-126">Options</span><span class="sxs-lookup"><span data-stu-id="4245d-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="4245d-127">Sources NuGet à utiliser dans la recherche de packages plus récents.</span><span class="sxs-lookup"><span data-stu-id="4245d-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="4245d-128">Nécessite l’option `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="4245d-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="4245d-129">Affiche uniquement les packages applicables au [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="4245d-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="4245d-130">Pour spécifier plusieurs frameworks, exécutez l’option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4245d-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="4245d-131">Par exemple : `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4245d-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4245d-132">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4245d-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="4245d-133">Prend en compte uniquement les packages avec un numéro de version majeure correspondant quand vous recherchez des packages plus récents.</span><span class="sxs-lookup"><span data-stu-id="4245d-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="4245d-134">Nécessite l’option `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="4245d-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="4245d-135">Prend en compte uniquement les packages avec des numéros de version majeure et mineure correspondants quand vous recherchez des packages plus récents.</span><span class="sxs-lookup"><span data-stu-id="4245d-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="4245d-136">Nécessite l’option `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="4245d-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="4245d-137">Prend en compte les packages avec des préversions quand vous recherchez des packages plus récents.</span><span class="sxs-lookup"><span data-stu-id="4245d-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="4245d-138">Nécessite l’option `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="4245d-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="4245d-139">Liste les packages transitifs, en plus des packages de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="4245d-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="4245d-140">Si vous spécifiez cette option, vous obtenez une liste des packages dont dépendent les packages de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="4245d-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="4245d-141">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4245d-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="4245d-142">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="4245d-142">For example, to complete authentication.</span></span> <span data-ttu-id="4245d-143">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="4245d-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="4245d-144">Répertorie les packages avec des versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="4245d-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="4245d-145">Sources NuGet à utiliser dans la recherche de packages plus récents.</span><span class="sxs-lookup"><span data-stu-id="4245d-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="4245d-146">Nécessite l’option `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="4245d-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="4245d-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="4245d-147">Examples</span></span>

- <span data-ttu-id="4245d-148">Répertorier les références de packages d’un projet spécifique :</span><span class="sxs-lookup"><span data-stu-id="4245d-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="4245d-149">Répertorier les références de packages avec des versions plus récentes, y compris des versions préliminaires :</span><span class="sxs-lookup"><span data-stu-id="4245d-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="4245d-150">Répertorier les références de packages pour un framework cible spécifique :</span><span class="sxs-lookup"><span data-stu-id="4245d-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
