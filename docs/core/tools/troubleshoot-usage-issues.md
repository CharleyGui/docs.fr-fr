---
title: Problème .NET Problèmes d’utilisation d’outils de base
description: Découvrez les problèmes communs lors de l’exécution des outils .NET Core et des solutions possibles.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146448"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="d8e2e-103">Problème .NET Problèmes d’utilisation d’outils de base</span><span class="sxs-lookup"><span data-stu-id="d8e2e-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="d8e2e-104">Vous pourriez rencontrer des problèmes lorsque vous essayez d’installer ou d’exécuter un outil .NET Core, qui peut être un outil global ou un outil local.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="d8e2e-105">Cet article décrit les causes profondes communes et certaines solutions possibles.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="d8e2e-106">L’outil de base .NET installé ne fonctionne pas</span><span class="sxs-lookup"><span data-stu-id="d8e2e-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="d8e2e-107">Lorsqu’un outil .NET Core ne fonctionne pas, il est fort probable que vous ayez rencontré l’un des problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="d8e2e-108">Le fichier exécutable pour l’outil n’a pas été trouvé.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="d8e2e-109">La version correcte du temps d’exécution .NET Core n’a pas été trouvée.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="d8e2e-110">Fichier exécutable non trouvé</span><span class="sxs-lookup"><span data-stu-id="d8e2e-110">Executable file not found</span></span>

<span data-ttu-id="d8e2e-111">Si le fichier exécutable n’est pas trouvé, vous verrez un message similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="d8e2e-112">Le nom de l’exécutable détermine comment vous invoquez l’outil.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="d8e2e-113">Le tableau suivant décrit le format :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-113">The following table describes the format:</span></span>

| <span data-ttu-id="d8e2e-114">Format de nom exécutable</span><span class="sxs-lookup"><span data-stu-id="d8e2e-114">Executable name format</span></span>  | <span data-ttu-id="d8e2e-115">Format d’invocation</span><span class="sxs-lookup"><span data-stu-id="d8e2e-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="d8e2e-116">Outils globaux</span><span class="sxs-lookup"><span data-stu-id="d8e2e-116">Global tools</span></span>

  <span data-ttu-id="d8e2e-117">Des outils globaux peuvent être installés dans l’annuaire par défaut ou dans un endroit spécifique.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="d8e2e-118">Les répertoires par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-118">The default directories are:</span></span>

  | <span data-ttu-id="d8e2e-119">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="d8e2e-119">OS</span></span>          | <span data-ttu-id="d8e2e-120">Path</span><span class="sxs-lookup"><span data-stu-id="d8e2e-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="d8e2e-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="d8e2e-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="d8e2e-122"> Windows</span><span class="sxs-lookup"><span data-stu-id="d8e2e-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="d8e2e-123">Si vous essayez d’exécuter un outil `PATH` global, vérifiez que la variable d’environnement sur votre machine contient le chemin où vous avez installé l’outil global et que l’exécutable est dans ce sens.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="d8e2e-124">Le CLI core .NET essaie d’ajouter l’emplacement par défaut à la variable d’environnement PATH sur sa première utilisation.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="d8e2e-125">Cependant, il existe certains scénarios où l’emplacement pourrait ne pas être ajouté à PATH automatiquement:</span><span class="sxs-lookup"><span data-stu-id="d8e2e-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="d8e2e-126">Si vous utilisez Linux et que vous avez installé le .NET Core SDK à l’aide de fichiers *.tar.gz* et non pas apt-get ou rpm.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="d8e2e-127">Si vous utilisez macOS 10.15 "Catalina" ou des versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="d8e2e-128">Si vous utilisez macOS 10.14 "Mojave" ou des versions antérieures, et vous avez installé le .NET Core SDK en utilisant des fichiers *.tar.gz* et non *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="d8e2e-129">Si vous avez installé le .NET Core 3.0 SDK et que vous avez défini la variable de l’environnement `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` à `false`.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="d8e2e-130">Si vous avez installé .NET Core 2.2 SDK ou des `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` versions `true`antérieures, et que vous avez défini la variable de l’environnement à .</span><span class="sxs-lookup"><span data-stu-id="d8e2e-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="d8e2e-131">Dans ces scénarios ou si `--tool-path` vous `PATH` avez spécifié l’option, la variable d’environnement sur votre machine ne contient pas automatiquement le chemin où vous avez installé l’outil global.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="d8e2e-132">Dans ce cas, appendicez l’emplacement de l’outil (par exemple) `$HOME/.dotnet/tools`à la variable d’environnement `PATH` en utilisant n’importe quelle méthode que votre coquille fournit pour mettre à jour les variables de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="d8e2e-133">Pour plus d’informations, voir [.NET Core tools](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d8e2e-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="d8e2e-134">Outils locaux</span><span class="sxs-lookup"><span data-stu-id="d8e2e-134">Local tools</span></span>

  <span data-ttu-id="d8e2e-135">Si vous essayez d’exécuter un outil local, vérifiez qu’il existe un fichier manifeste appelé *dotnet-tools.json* dans l’annuaire actuel ou l’un de ses répertoires parent.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="d8e2e-136">Ce fichier peut également vivre sous un dossier nommé *.config* n’importe où dans la hiérarchie du dossier de projet, au lieu du dossier de racine.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="d8e2e-137">Si *dotnet-tools.json* existe, ouvrez-le et vérifiez l’outil que vous essayez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="d8e2e-138">Si le fichier ne contient `"isRoot": true`pas d’entrée pour , puis vérifiez également plus loin dans la hiérarchie de fichiers pour les fichiers manifestes d’outils supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="d8e2e-139">Si vous essayez d’exécuter un outil .NET Core qui a été installé avec un chemin spécifié, vous devez inclure ce chemin lors de l’utilisation de l’outil.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="d8e2e-140">Un exemple d’utilisation d’un outil installé est :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="d8e2e-141">Temps d’exécution non trouvé</span><span class="sxs-lookup"><span data-stu-id="d8e2e-141">Runtime not found</span></span>

<span data-ttu-id="d8e2e-142">.NET Les outils de base sont [des applications dépendantes du cadre,](../deploying/index.md#publish-runtime-dependent)ce qui signifie qu’ils s’appuient sur un temps d’exécution .NET Core installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="d8e2e-143">Si le temps d’exécution prévu n’est pas trouvé, ils suivent les règles normales .NET Core runtime roll-forward telles que:</span><span class="sxs-lookup"><span data-stu-id="d8e2e-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="d8e2e-144">Une application restaure par progression le correctif le plus élevé de la version principale et secondaire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="d8e2e-145">S’il n’y a pas de temps d’exécution correspondant avec un numéro de version majeur et mineur correspondant, la prochaine version mineure supérieure est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="d8e2e-146">Une restauration par progression ne se produit pas entre des préversions du runtime ou entre des préversions et des versions finales.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="d8e2e-147">Ainsi, les outils .NET Core créés à l’aide de versions de prévisualisation doivent être reconstruits et republiés par l’auteur et réinstallés.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="d8e2e-148">Roll-forward ne se produira pas par défaut dans deux scénarios courants :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="d8e2e-149">Seules des versions inférieures de l’exécution sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="d8e2e-150">Roll-forward ne sélectionne que les versions ultérieures de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="d8e2e-151">Seules des versions majeures supérieures du temps d’exécution sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="d8e2e-152">Roll-forward ne franchit pas les frontières des versions majeures.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="d8e2e-153">Si une application ne peut pas trouver un temps d’exécution approprié, elle ne s’exécute pas et signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="d8e2e-154">Vous pouvez savoir quels arrêts .NET Core sont installés sur votre machine à l’aide d’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="d8e2e-155">Si vous pensez que l’outil doit prendre en charge la version en temps d’exécution que vous avez actuellement installé, vous pouvez contacter l’auteur de l’outil et voir s’ils peuvent mettre à jour le numéro de version ou multi-cible.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="d8e2e-156">Une fois qu’ils ont recompilé et réédité leur paquet d’outils à NuGet avec un numéro de version mis à jour, vous pouvez mettre à jour votre copie.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="d8e2e-157">Bien que cela ne se produise pas, la solution la plus rapide pour vous est d’installer une version du temps d’exécution qui fonctionnerait avec l’outil que vous essayez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="d8e2e-158">Pour télécharger une version spécifique .NET Core runtime, visitez la [page de téléchargement .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="d8e2e-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="d8e2e-159">Si vous installez le SDK core .NET à un emplacement `DOTNET_ROOT` non par défaut, `dotnet` vous devez définir la variable d’environnement à l’annuaire qui contient l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="d8e2e-160">l’installation d’outil de base de net-NET échoue</span><span class="sxs-lookup"><span data-stu-id="d8e2e-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="d8e2e-161">Il ya un certain nombre de raisons pour lesquelles l’installation d’un outil mondial ou local .NET Core peut échouer.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="d8e2e-162">Lorsque l’installation de l’outil échoue, vous verrez un message similaire à celui suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2e-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="d8e2e-163">Pour aider à diagnostiquer ces défaillances, les messages NuGet sont affichés directement à l’utilisateur, ainsi que le message précédent.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="d8e2e-164">Le message NuGet peut vous aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="d8e2e-165">Exécution de nommage de paquet</span><span class="sxs-lookup"><span data-stu-id="d8e2e-165">Package naming enforcement</span></span>

<span data-ttu-id="d8e2e-166">Microsoft a changé ses conseils sur l’ID package pour les outils, résultant en un certain nombre d’outils ne sont pas trouvés avec le nom prévu.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="d8e2e-167">La nouvelle orientation est que tous les outils Microsoft soient préfixés avec "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="d8e2e-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="d8e2e-168">Ce préfixe est réservé et ne peut être utilisé que pour les paquets signés avec un certificat autorisé par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="d8e2e-169">Pendant la transition, certains outils Microsoft auront l’ancienne forme de l’ID paquet, tandis que d’autres auront le nouveau formulaire:</span><span class="sxs-lookup"><span data-stu-id="d8e2e-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="d8e2e-170">Au fur et à mesure que les identifiants de paquet sont mis à jour, vous devrez modifier le nouvel ID du paquet pour obtenir les dernières mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="d8e2e-171">Les paquets avec le nom simplifié de l’outil seront dépréciés.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="d8e2e-172">Extrait des versions</span><span class="sxs-lookup"><span data-stu-id="d8e2e-172">Preview releases</span></span>

* <span data-ttu-id="d8e2e-173">Vous essayez d’installer une version de prévisualisation et n’avez pas utilisé l’option `--version` pour spécifier la version.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="d8e2e-174">.NET Les outils de base qui sont en prévisualisation doivent être spécifiés avec une partie du nom pour indiquer qu’ils sont en prévisualisation.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="d8e2e-175">Vous n’avez pas besoin d’inclure l’aperçu complet.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="d8e2e-176">En supposant que les numéros de version sont dans le format prévu, vous pouvez utiliser quelque chose comme l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="d8e2e-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="d8e2e-177">Le paquet n’est pas un outil .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8e2e-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="d8e2e-178">Un paquet NuGet de ce nom a été trouvé, mais ce n’était pas un outil .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="d8e2e-179">Si vous essayez d’installer un package NuGet qui est un paquet NuGet régulier et non un outil .NET Core, vous verrez une erreur similaire à ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="d8e2e-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="d8e2e-180">NU1212: Combinaison de projets invalides pour `<ToolName>`.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="d8e2e-181">Le style du projet DotnetToolReference ne peut contenir que des références du type DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="d8e2e-182">L’alimentation NuGet ne peut pas être consultée</span><span class="sxs-lookup"><span data-stu-id="d8e2e-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="d8e2e-183">Le flux NuGet requis ne peut pas être consulté, peut-être en raison d’un problème de connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="d8e2e-184">L’installation d’outils nécessite l’accès à l’alimentation NuGet qui contient le paquet d’outils.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="d8e2e-185">Il échoue si le flux n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="d8e2e-186">Vous pouvez modifier `nuget.config`les flux `nuget.config` avec, demander un fichier `--add-source` spécifique, ou spécifier des flux supplémentaires avec le commutateur.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="d8e2e-187">Par défaut, NuGet lance une erreur pour tout flux qui ne peut pas se connecter.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="d8e2e-188">Le `--ignore-failed-sources` drapeau peut sauter ces sources non accessibles.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="d8e2e-189">Identifiant de paquet incorrect</span><span class="sxs-lookup"><span data-stu-id="d8e2e-189">Package ID incorrect</span></span>

* <span data-ttu-id="d8e2e-190">Vous avez mal interprété le nom de l’outil.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="d8e2e-191">Une raison commune de l’échec est que le nom de l’outil n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="d8e2e-192">Cela peut se produire en raison de mauvaisty, ou parce que l’outil a bougé ou a été déprécié.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="d8e2e-193">Pour les outils sur NuGet.org, une façon de s’assurer que vous avez le nom correct est de rechercher l’outil à NuGet.org et copier la commande d’installation.</span><span class="sxs-lookup"><span data-stu-id="d8e2e-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8e2e-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8e2e-194">See also</span></span>

* [<span data-ttu-id="d8e2e-195">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="d8e2e-195">.NET Core tools</span></span>](global-tools.md)
