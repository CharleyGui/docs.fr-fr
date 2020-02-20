---
title: Résoudre les problèmes d’utilisation de l’outil .NET Core
description: Découvrez les problèmes courants liés à l’exécution des outils .NET Core et des solutions possibles.
author: kdollard
ms.date: 09/23/2019
ms.openlocfilehash: 45139c3441b84964b937d5d1cc63a018f8d1f0fb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451075"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="8cd3a-103">Résoudre les problèmes d’utilisation de l’outil .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd3a-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="8cd3a-104">Vous risquez de rencontrer des problèmes lors de la tentative d’installation ou d’exécution d’un outil .NET Core, qui peut être un outil Global ou un outil local.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="8cd3a-105">Cet article décrit les causes principales et les solutions possibles.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="8cd3a-106">L’exécution de l’outil .NET Core installé échoue</span><span class="sxs-lookup"><span data-stu-id="8cd3a-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="8cd3a-107">En cas d’échec de l’exécution d’un outil .NET Core, vous avez probablement rencontré l’un des problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="8cd3a-108">Le fichier exécutable de l’outil est introuvable.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="8cd3a-109">La version correcte du Runtime .NET Core est introuvable.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="8cd3a-110">Fichier exécutable introuvable</span><span class="sxs-lookup"><span data-stu-id="8cd3a-110">Executable file not found</span></span>

<span data-ttu-id="8cd3a-111">Si le fichier exécutable est introuvable, un message semblable au suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="8cd3a-112">Le nom de l’exécutable détermine la façon dont vous appelez l’outil.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="8cd3a-113">Le tableau suivant décrit le format :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-113">The following table describes the format:</span></span>

| <span data-ttu-id="8cd3a-114">Format du nom de l’exécutable</span><span class="sxs-lookup"><span data-stu-id="8cd3a-114">Executable name format</span></span>  | <span data-ttu-id="8cd3a-115">Format d’appel</span><span class="sxs-lookup"><span data-stu-id="8cd3a-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="8cd3a-116">Outils globaux</span><span class="sxs-lookup"><span data-stu-id="8cd3a-116">Global tools</span></span>

    <span data-ttu-id="8cd3a-117">Les outils globaux peuvent être installés dans le répertoire par défaut ou dans un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="8cd3a-118">Les répertoires par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-118">The default directories are:</span></span>

    | <span data-ttu-id="8cd3a-119">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="8cd3a-119">OS</span></span>          | <span data-ttu-id="8cd3a-120">Path</span><span class="sxs-lookup"><span data-stu-id="8cd3a-120">Path</span></span>                          |
    |-------------|-------------------------------|
    | <span data-ttu-id="8cd3a-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="8cd3a-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
    | <span data-ttu-id="8cd3a-122">Windows</span><span class="sxs-lookup"><span data-stu-id="8cd3a-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

    <span data-ttu-id="8cd3a-123">Si vous essayez d’exécuter un outil Global, vérifiez que la variable d’environnement `PATH` sur votre ordinateur contient le chemin d’accès où vous avez installé l’outil Global et que l’exécutable se trouve dans ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

    <span data-ttu-id="8cd3a-124">CLI .NET Core essaie d’ajouter les emplacements par défaut à la variable d’environnement PATH lors de sa première utilisation.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-124">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="8cd3a-125">Toutefois, il existe deux scénarios dans lesquels l’emplacement ne peut pas être ajouté automatiquement au chemin. vous devez donc modifier le chemin d’accès pour le configurer pour les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-125">However, there are a couple of scenarios where the location might not be added to PATH automatically, so you'll have to edit PATH to configure it for the following cases:</span></span>

  * <span data-ttu-id="8cd3a-126">Si vous utilisez Linux et que vous avez installé le kit SDK .NET Core à l’aide de fichiers *. tar. gz* et non de apt ou RPM.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="8cd3a-127">Si vous utilisez macOS 10,15 « Catalina » ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="8cd3a-128">Si vous utilisez macOS 10,14 « Mojave » ou des versions antérieures, et que vous avez installé le kit SDK .NET Core à l’aide des fichiers *. tar. gz* et non *. pkg*.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="8cd3a-129">Si vous avez installé le kit de développement logiciel (SDK) .NET Core 3,0 et que vous avez défini la variable d’environnement `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` sur `false`.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="8cd3a-130">Si vous avez installé le kit de développement logiciel (SDK) .NET Core 2,2 ou des versions antérieures, et que vous avez défini la variable d’environnement `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="8cd3a-131">Pour plus d’informations sur les outils globaux, consultez [vue d’ensemble des outils globaux .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8cd3a-131">For more information about global tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

* <span data-ttu-id="8cd3a-132">Outils locaux</span><span class="sxs-lookup"><span data-stu-id="8cd3a-132">Local tools</span></span>

  <span data-ttu-id="8cd3a-133">Si vous essayez d’exécuter un outil local, vérifiez qu’il existe un fichier manifeste nommé *dotnet-Tools. JSON* dans le répertoire actif ou dans l’un de ses répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-133">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="8cd3a-134">Ce fichier peut également résider sous un dossier nommé *. config* n’importe où dans l’arborescence des dossiers du projet, et non dans le dossier racine.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-134">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="8cd3a-135">Si *dotnet-Tools. JSON* existe, ouvrez-le et recherchez l’outil que vous essayez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-135">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="8cd3a-136">Si le fichier ne contient pas d’entrée pour `"isRoot": true`, activez également la case à cocher plus haut dans la hiérarchie des fichiers pour les fichiers de manifeste d’outils supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-136">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="8cd3a-137">Si vous essayez d’exécuter un outil .NET Core qui a été installé avec un chemin d’accès spécifié, vous devez inclure ce chemin d’accès lors de l’utilisation de l’outil.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-137">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="8cd3a-138">Voici un exemple d’utilisation d’un outil d’installation de chemin d’accès d’outil :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-138">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="8cd3a-139">Runtime introuvable</span><span class="sxs-lookup"><span data-stu-id="8cd3a-139">Runtime not found</span></span>

<span data-ttu-id="8cd3a-140">Les outils .NET Core sont des [applications dépendantes du Framework](../deploying/index.md#publish-runtime-dependent), ce qui signifie qu’elles s’appuient sur un Runtime .net Core installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-140">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="8cd3a-141">Si le runtime attendu est introuvable, ils suivent les règles de restauration par progression normales du Runtime .NET Core, telles que :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-141">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="8cd3a-142">Une application restaure par progression le correctif le plus élevé de la version principale et secondaire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-142">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="8cd3a-143">S’il n’existe aucun Runtime correspondant avec un numéro de version principale et secondaire correspondant, la version mineure supérieure suivante est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-143">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="8cd3a-144">Une restauration par progression ne se produit pas entre des préversions du runtime ou entre des préversions et des versions finales.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-144">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="8cd3a-145">Ainsi, les outils .NET Core créés à l’aide des versions préliminaires doivent être reconstruits et republiés par l’auteur et réinstallés.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-145">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="8cd3a-146">La restauration par progression ne se produit pas par défaut dans deux scénarios courants :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-146">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="8cd3a-147">Seules les versions inférieures du runtime sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-147">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="8cd3a-148">La restauration par progression sélectionne uniquement les versions ultérieures du Runtime.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-148">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="8cd3a-149">Seules les versions majeures les plus importantes du runtime sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-149">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="8cd3a-150">La restauration par progression n’entre pas dans les limites de version principales.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-150">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="8cd3a-151">Si une application ne parvient pas à trouver un Runtime approprié, elle ne parvient pas à s’exécuter et signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-151">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="8cd3a-152">Vous pouvez déterminer quels runtimes .NET Core sont installés sur votre ordinateur à l’aide de l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-152">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="8cd3a-153">Si vous pensez que l’outil doit prendre en charge la version du runtime que vous avez installée actuellement, vous pouvez contacter l’auteur de l’outil et voir s’il peut mettre à jour le numéro de version ou le multi-cible.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-153">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="8cd3a-154">Une fois qu’ils ont recompilé et republié leur package d’outils dans NuGet avec un numéro de version mis à jour, vous pouvez mettre à jour votre copie.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-154">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="8cd3a-155">Bien que cela ne se produise pas, la solution la plus rapide consiste à installer une version du runtime qui fonctionnerait avec l’outil que vous essayez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-155">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="8cd3a-156">Pour télécharger une version spécifique du Runtime .NET Core, visitez la [page de téléchargement de .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8cd3a-156">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="8cd3a-157">Si vous installez le kit SDK .NET Core à un emplacement autre que celui par défaut, vous devez définir la variable d’environnement `DOTNET_ROOT` sur le répertoire qui contient le fichier exécutable `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-157">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="8cd3a-158">Échec de l’installation de l’outil .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd3a-158">.NET Core tool installation fails</span></span>

<span data-ttu-id="8cd3a-159">Il existe plusieurs raisons pour lesquelles l’installation d’un outil Global ou local .NET Core peut échouer.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-159">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="8cd3a-160">Lorsque l’installation de l’outil échoue, un message semblable à celui-ci s’affiche :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-160">When the tool installation fails, you'll see a message similar to following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="8cd3a-161">Pour faciliter le diagnostic de ces échecs, les messages NuGet s’affichent directement à l’utilisateur, ainsi que le message précédent.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-161">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="8cd3a-162">Le message NuGet peut vous aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-162">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="8cd3a-163">Mise en application des noms de packages</span><span class="sxs-lookup"><span data-stu-id="8cd3a-163">Package naming enforcement</span></span>

<span data-ttu-id="8cd3a-164">Microsoft a modifié ses conseils sur l’ID de package pour les outils, ce qui a entraîné un certain nombre d’outils introuvables avec le nom prédit.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-164">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="8cd3a-165">La nouvelle recommandation est que tous les outils Microsoft sont préfixés avec « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="8cd3a-165">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="8cd3a-166">Ce préfixe est réservé et ne peut être utilisé que pour les packages signés avec un certificat autorisé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-166">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="8cd3a-167">Pendant la transition, certains outils Microsoft auront l’ancienne forme de l’ID de package, tandis que d’autres auront le nouveau formulaire :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-167">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="8cd3a-168">À mesure que les ID de package sont mis à jour, vous devez passer au nouvel ID de package pour récupérer les dernières mises à jour.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-168">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="8cd3a-169">Les packages avec le nom de l’outil simplifié seront déconseillés.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-169">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="8cd3a-170">Versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="8cd3a-170">Preview releases</span></span>

* <span data-ttu-id="8cd3a-171">Vous tentez d’installer une version préliminaire et vous n’avez pas utilisé l’option `--version` pour spécifier la version.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-171">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="8cd3a-172">Les outils .NET Core qui sont en version préliminaire doivent être spécifiés avec une partie du nom pour indiquer qu’ils sont en préversion.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-172">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="8cd3a-173">Vous n’avez pas besoin d’inclure la version préliminaire entière.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-173">You don't need to include the entire preview.</span></span> <span data-ttu-id="8cd3a-174">En supposant que les numéros de version sont au format attendu, vous pouvez utiliser une commande semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-174">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

> [!NOTE]
> <span data-ttu-id="8cd3a-175">L’équipe CLI .NET Core prévoit d’ajouter un commutateur `--preview` dans une prochaine version pour faciliter ce travail.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-175">The .NET Core CLI team is planning to add a `--preview` switch in a future release to make this easier.</span></span>

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="8cd3a-176">Le package n’est pas un outil .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd3a-176">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="8cd3a-177">Un package NuGet portant ce nom a été trouvé, mais il ne s’agissait pas d’un outil .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-177">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="8cd3a-178">Si vous essayez d’installer un package NuGet qui est un package NuGet standard et non un outil .NET Core, une erreur semblable à la suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="8cd3a-178">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="8cd3a-179">NU1212 : combinaison projet-package non valide pour `<ToolName>`.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-179">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="8cd3a-180">Le style de projet DotnetToolReference peut uniquement contenir des références du type DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-180">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="8cd3a-181">Impossible d’accéder au flux NuGet</span><span class="sxs-lookup"><span data-stu-id="8cd3a-181">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="8cd3a-182">Le flux NuGet requis n’est pas accessible, peut-être en raison d’un problème de connexion à Internet.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-182">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="8cd3a-183">L’installation de l’outil nécessite l’accès au flux NuGet qui contient le package d’outils.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-183">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="8cd3a-184">Elle échoue si le flux n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-184">It fails if the feed isn't available.</span></span> <span data-ttu-id="8cd3a-185">Vous pouvez modifier les flux avec `nuget.config`, demander un fichier `nuget.config` spécifique ou spécifier des flux supplémentaires avec le commutateur `--add-source`.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-185">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="8cd3a-186">Par défaut, NuGet génère une erreur pour tout flux qui ne peut pas se connecter.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-186">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="8cd3a-187">L’indicateur `--ignore-failed-sources` peut ignorer ces sources qui ne sont pas accessibles.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-187">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="8cd3a-188">ID de package incorrect</span><span class="sxs-lookup"><span data-stu-id="8cd3a-188">Package ID incorrect</span></span>

* <span data-ttu-id="8cd3a-189">Vous avez tapé le nom de l’outil de façon invoulue.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-189">You mistyped the name of the tool.</span></span>

<span data-ttu-id="8cd3a-190">L’échec est généralement dû au fait que le nom de l’outil n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-190">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="8cd3a-191">Cela peut se produire en raison d’une saisie incorrecte ou parce que l’outil a été déplacé ou déconseillé.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-191">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="8cd3a-192">Pour les outils sur NuGet.org, l’une des façons de s’assurer que le nom est correct consiste à Rechercher l’outil sur NuGet.org et à copier la commande d’installation.</span><span class="sxs-lookup"><span data-stu-id="8cd3a-192">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cd3a-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cd3a-193">See also</span></span>

* [<span data-ttu-id="8cd3a-194">Vue d’ensemble des outils globaux .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd3a-194">.NET Core Global Tools overview</span></span>](global-tools.md)
