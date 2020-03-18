---
title: Outil désinstaller
description: Un aperçu de l’outil .NET Core Uninstall, un outil guidé qui permet le nettoyage contrôlé des SDKs et des runtimes .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847032"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="ffabb-103">Outil de désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="ffabb-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="ffabb-104">[L’outil .NET Core Uninstall](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) vous permet de supprimer .NET Core SDKs et Runtimes d’un système.</span><span class="sxs-lookup"><span data-stu-id="ffabb-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="ffabb-105">Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ffabb-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="ffabb-106">L’outil prend en charge Windows et macOS.</span><span class="sxs-lookup"><span data-stu-id="ffabb-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="ffabb-107">Pour le moment, Linux n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ffabb-107">Linux is currently not supported.</span></span>

<span data-ttu-id="ffabb-108">Sur Windows, l’outil ne peut désinstaller les SDK et les Runtimes qui ont été installés à l’aide d’un des installateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="ffabb-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="ffabb-109">Le .NET Core SDK et l’installateur de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ffabb-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="ffabb-110">L’installateur Visual Studio en versions antérieures à la version 16.3 de Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ffabb-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="ffabb-111">Sur macOS, l’outil ne peut désinstaller les SDK et les temps d’exécution situés dans le dossier */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="ffabb-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="ffabb-112">En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les SDKs de base .NET et les temps d’exécution sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="ffabb-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="ffabb-113">Vous pouvez `dotnet --info` utiliser la commande pour trouver tous les SDKs de base .NET et les temps d’exécution installés, y compris les SDK et les temps d’exécution que cet outil ne peut pas supprimer.</span><span class="sxs-lookup"><span data-stu-id="ffabb-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="ffabb-114">La `dotnet-core-uninstall list` commande affiche quels SDKs peuvent être désinstallés avec l’outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="ffabb-115">Installer l’outil</span><span class="sxs-lookup"><span data-stu-id="ffabb-115">Install the tool</span></span>

<span data-ttu-id="ffabb-116">Vous pouvez télécharger l’outil .NET Core Uninstall à partir [d’ici](https://aka.ms/dotnet-core-uninstall-tool) et trouver le code source au référentiel [GitHub dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="ffabb-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="ffabb-117">L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ffabb-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="ffabb-118">Par conséquent, il devrait être installé dans un répertoire protégé par l’écriture tels que *les fichiers de programme C: 'program* sur Windows ou */usr/local/bin* sur macOS.</span><span class="sxs-lookup"><span data-stu-id="ffabb-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="ffabb-119">Voir aussi [Accès élevé pour les commandes dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="ffabb-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="ffabb-120">Pour plus d’informations, voir les [instructions d’installation détaillées](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="ffabb-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="ffabb-121">Exécuter l’outil</span><span class="sxs-lookup"><span data-stu-id="ffabb-121">Run the tool</span></span>

<span data-ttu-id="ffabb-122">Les étapes suivantes montrent l’approche recommandée pour l’exécution de l’outil de désinstallation :</span><span class="sxs-lookup"><span data-stu-id="ffabb-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="ffabb-123">Étape 1 - Affichage installé .NET Core SDKs et runtimes</span><span class="sxs-lookup"><span data-stu-id="ffabb-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="ffabb-124">Étape 2 - Faire une course à sec</span><span class="sxs-lookup"><span data-stu-id="ffabb-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="ffabb-125">Étape 3 - Uninstall .NET Core SDKs and Runtimes</span><span class="sxs-lookup"><span data-stu-id="ffabb-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="ffabb-126">Étape 4 - Supprimer le dossier de repli NuGet (facultatif)</span><span class="sxs-lookup"><span data-stu-id="ffabb-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="ffabb-127">Étape 1 - Affichage installé .NET Core SDKs et runtimes</span><span class="sxs-lookup"><span data-stu-id="ffabb-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="ffabb-128">La `dotnet-core-uninstall list` commande répertorie les SDKs et les temps d’exécution .NET core installés qui peuvent être supprimés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="ffabb-129">Certains SDK et les durées d’exécution peuvent être nécessaires par Visual Studio et ils sont affichés avec une note de pourquoi il n’est pas recommandé de les désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ffabb-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="ffabb-130">**liste dotnet-core-uninstall**</span><span class="sxs-lookup"><span data-stu-id="ffabb-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ffabb-131">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ffabb-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="ffabb-132">Options</span><span class="sxs-lookup"><span data-stu-id="ffabb-132">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ffabb-133">Windows</span><span class="sxs-lookup"><span data-stu-id="ffabb-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="ffabb-134">Répertorie tous les temps d’exécution ASP.NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ffabb-135">Répertorie tous les forfaits .NET Core et les forfaits d’hébergement qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="ffabb-136">Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-137">Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-138">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-138">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-140">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ffabb-141">Répertorie tous les SDKs et les runtimes de base x64 .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="ffabb-142">Répertorie tous les SDKs et les runtimes de base x86 .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ffabb-143">macOS</span><span class="sxs-lookup"><span data-stu-id="ffabb-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="ffabb-144">Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-145">Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="ffabb-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-146">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-146">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-147">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-148">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="ffabb-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="ffabb-149">Examples</span></span>

* <span data-ttu-id="ffabb-150">Énumérez tous les SDKs de base de .NET et les temps d’exécution qui peuvent être supprimés avec cet outil :</span><span class="sxs-lookup"><span data-stu-id="ffabb-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="ffabb-151">Liste tous les X64 .NET Core SDKs et runtimes:</span><span class="sxs-lookup"><span data-stu-id="ffabb-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="ffabb-152">Liste tous les X86 .NET Core SDKs:</span><span class="sxs-lookup"><span data-stu-id="ffabb-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="ffabb-153">Étape 2 - Faire une course à sec</span><span class="sxs-lookup"><span data-stu-id="ffabb-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="ffabb-154">Les `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` commandes et les commandes affichent les SDKs et les temps d’exécution .NET Core qui seront supprimés en fonction des options fournies sans effectuer le désinstallation.</span><span class="sxs-lookup"><span data-stu-id="ffabb-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="ffabb-155">Ces commandes sont synonymes.</span><span class="sxs-lookup"><span data-stu-id="ffabb-155">These commands are synonyms.</span></span>

<span data-ttu-id="ffabb-156">**dotnet-core-uninstall dry-run et dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="ffabb-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ffabb-157">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ffabb-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="ffabb-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="ffabb-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="ffabb-159">La version spécifiée pour désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ffabb-159">The specified version to uninstall.</span></span> <span data-ttu-id="ffabb-160">Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="ffabb-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="ffabb-161">Les fichiers de réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ffabb-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="ffabb-162">Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ffabb-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="ffabb-163">Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="ffabb-164">Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.</span><span class="sxs-lookup"><span data-stu-id="ffabb-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="ffabb-165">Options</span><span class="sxs-lookup"><span data-stu-id="ffabb-165">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ffabb-166">Windows</span><span class="sxs-lookup"><span data-stu-id="ffabb-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="ffabb-167">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffabb-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ffabb-168">Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="ffabb-169">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ffabb-170">Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ffabb-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ffabb-171">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ffabb-172">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ffabb-173">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="ffabb-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ffabb-174">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="ffabb-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ffabb-175">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="ffabb-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="ffabb-176">Supprime ASP.NET les temps d’exécution Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ffabb-177">Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ffabb-178">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ffabb-179">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-180">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-181">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-181">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-182">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-183">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ffabb-184">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="ffabb-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="ffabb-185">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="ffabb-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="ffabb-186">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffabb-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="ffabb-187">Remarques :</span><span class="sxs-lookup"><span data-stu-id="ffabb-187">Notes:</span></span>

1. <span data-ttu-id="ffabb-188">Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ffabb-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="ffabb-189">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="ffabb-190">Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ffabb-191">macOS</span><span class="sxs-lookup"><span data-stu-id="ffabb-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="ffabb-192">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffabb-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ffabb-193">Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="ffabb-194">La version spécifiée restera.</span><span class="sxs-lookup"><span data-stu-id="ffabb-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ffabb-195">Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ffabb-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ffabb-196">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ffabb-197">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ffabb-198">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="ffabb-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ffabb-199">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="ffabb-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ffabb-200">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="ffabb-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ffabb-201">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ffabb-202">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-203">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-204">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-204">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-205">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-206">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="ffabb-207">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="ffabb-208">Remarques :</span><span class="sxs-lookup"><span data-stu-id="ffabb-208">Notes:</span></span>

1. <span data-ttu-id="ffabb-209">Exactement un `--sdk` `--runtime` de et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ffabb-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="ffabb-210">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="ffabb-211">Exemples</span><span class="sxs-lookup"><span data-stu-id="ffabb-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="ffabb-212">Par défaut, les SDKs de base .NET et les temps d’exécution qui `dotnet-core-uninstall dry-run` peuvent être exigés par Visual Studio ou d’autres SDK ne sont pas inclus dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="ffabb-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="ffabb-213">Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent ne pas être inclus dans la sortie, selon l’état de la machine.</span><span class="sxs-lookup"><span data-stu-id="ffabb-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="ffabb-214">Pour inclure tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`</span><span class="sxs-lookup"><span data-stu-id="ffabb-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="ffabb-215">Course sèche de l’élimination de tous les temps d’exécution .NET Core qui ont été remplacés par des correctifs plus élevés:</span><span class="sxs-lookup"><span data-stu-id="ffabb-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="ffabb-216">Course sèche de la suppression de tous les `2.2.301`SDKs .NET Core en dessous de la version :</span><span class="sxs-lookup"><span data-stu-id="ffabb-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="ffabb-217">Étape 3 - Uninstall .NET Core SDKs and Runtimes</span><span class="sxs-lookup"><span data-stu-id="ffabb-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="ffabb-218">`dotnet-core-uninstall remove`désinstaller .NET Core SDKs et Runtimes qui sont spécifiés par une collection d’options.</span><span class="sxs-lookup"><span data-stu-id="ffabb-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="ffabb-219">L’outil ne peut pas être utilisé pour désinstaller les SDK et les Runtimes avec la version 5.0 ou plus.</span><span class="sxs-lookup"><span data-stu-id="ffabb-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="ffabb-220">Depuis cet outil a un comportement destructeur, il est **fortement** recommandé que vous faites une course à sec avant d’exécuter la commande de suppression.</span><span class="sxs-lookup"><span data-stu-id="ffabb-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="ffabb-221">La course à sec vous montrera ce que les SDKs de `remove` base de .NET et les temps d’exécution seront supprimés lorsque vous utilisez la commande.</span><span class="sxs-lookup"><span data-stu-id="ffabb-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="ffabb-222">Se référer à [Dois-je supprimer une version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDKs et runtimes sont sûrs à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ffabb-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="ffabb-223">Rappelez-vous des avertissements suivants :</span><span class="sxs-lookup"><span data-stu-id="ffabb-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="ffabb-224">Cet outil peut désinstaller les versions du SDK `global.json` .NET Core qui sont requis par les fichiers sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="ffabb-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="ffabb-225">Vous pouvez réinstaller .NET Core SDKs à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="ffabb-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="ffabb-226">Cet outil peut désinstaller les versions du temps d’exécution .NET Core qui sont requis par des applications dépendantes du cadre de votre machine.</span><span class="sxs-lookup"><span data-stu-id="ffabb-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="ffabb-227">Vous pouvez réinstaller les temps d’exécution .NET Core à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="ffabb-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="ffabb-228">Cet outil peut désinstaller les versions du .NET Core SDK et le temps d’exécution sur lequel Visual Studio s’appuie.</span><span class="sxs-lookup"><span data-stu-id="ffabb-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="ffabb-229">Si vous cassez votre installation Visual Studio, exécutez "Repair" dans l’installateur Visual Studio pour revenir à un état de travail.</span><span class="sxs-lookup"><span data-stu-id="ffabb-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="ffabb-230">Par défaut, toutes les commandes conservent les SDKs et les temps d’exécution .NET Core qui peuvent être requis par Visual Studio ou d’autres SDK.</span><span class="sxs-lookup"><span data-stu-id="ffabb-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="ffabb-231">Ces SDK et runtimes peuvent être désinstallés en `--force` les énumérant explicitement comme arguments ou en utilisant l’option.</span><span class="sxs-lookup"><span data-stu-id="ffabb-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="ffabb-232">L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ffabb-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="ffabb-233">Exécutez l’outil dans une invite `sudo` de commande d’administrateur sur Windows et avec sur macOS.</span><span class="sxs-lookup"><span data-stu-id="ffabb-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="ffabb-234">L’élévation `dry-run` et `whatif` les commandes ne nécessitent pas d’élévation.</span><span class="sxs-lookup"><span data-stu-id="ffabb-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="ffabb-235">**dotnet-core-uninstall supprimer**</span><span class="sxs-lookup"><span data-stu-id="ffabb-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ffabb-236">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ffabb-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="ffabb-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="ffabb-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="ffabb-238">La version spécifiée pour désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ffabb-238">The specified version to uninstall.</span></span> <span data-ttu-id="ffabb-239">Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="ffabb-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="ffabb-240">Les fichiers de réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ffabb-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="ffabb-241">Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ffabb-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="ffabb-242">Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="ffabb-243">Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.</span><span class="sxs-lookup"><span data-stu-id="ffabb-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="ffabb-244">Options</span><span class="sxs-lookup"><span data-stu-id="ffabb-244">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ffabb-245">Windows</span><span class="sxs-lookup"><span data-stu-id="ffabb-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="ffabb-246">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffabb-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ffabb-247">Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="ffabb-248">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ffabb-249">Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ffabb-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ffabb-250">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ffabb-251">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ffabb-252">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="ffabb-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ffabb-253">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="ffabb-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ffabb-254">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="ffabb-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="ffabb-255">Supprime ASP.NET les temps d’exécution Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ffabb-256">Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ffabb-257">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ffabb-258">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-259">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-260">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-260">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-261">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-262">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ffabb-263">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="ffabb-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="ffabb-264">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="ffabb-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="ffabb-265">**`-y, --yes`** Exécutez la commande sans nécessiter de confirmation oui ou non.</span><span class="sxs-lookup"><span data-stu-id="ffabb-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="ffabb-266">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffabb-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="ffabb-267">Remarques :</span><span class="sxs-lookup"><span data-stu-id="ffabb-267">Notes:</span></span>

1. <span data-ttu-id="ffabb-268">Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ffabb-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="ffabb-269">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="ffabb-270">Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ffabb-271">macOS</span><span class="sxs-lookup"><span data-stu-id="ffabb-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="ffabb-272">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffabb-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ffabb-273">Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="ffabb-274">La version spécifiée restera.</span><span class="sxs-lookup"><span data-stu-id="ffabb-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ffabb-275">Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ffabb-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ffabb-276">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ffabb-277">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ffabb-278">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="ffabb-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ffabb-279">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="ffabb-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ffabb-280">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="ffabb-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ffabb-281">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ffabb-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ffabb-282">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ffabb-283">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="ffabb-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ffabb-284">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="ffabb-284">Sets the verbosity level.</span></span> <span data-ttu-id="ffabb-285">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ffabb-286">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-286">The default value is `normal`.</span></span>

* <span data-ttu-id="ffabb-287">**`-y, --yes`** Exécutez la commande sans nécessiter la confirmation de Y/N.</span><span class="sxs-lookup"><span data-stu-id="ffabb-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="ffabb-288">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="ffabb-289">Remarques :</span><span class="sxs-lookup"><span data-stu-id="ffabb-289">Notes:</span></span>

1. <span data-ttu-id="ffabb-290">Exactement un `--sdk` `--runtime` de et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ffabb-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="ffabb-291">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="ffabb-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="ffabb-292">Exemples</span><span class="sxs-lookup"><span data-stu-id="ffabb-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="ffabb-293">Par défaut, les SDK core .NET et les temps d’exécution qui peuvent être requis par Visual Studio ou d’autres SDK sont conservés.</span><span class="sxs-lookup"><span data-stu-id="ffabb-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="ffabb-294">Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent rester, selon l’état de la machine.</span><span class="sxs-lookup"><span data-stu-id="ffabb-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="ffabb-295">Pour supprimer tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`</span><span class="sxs-lookup"><span data-stu-id="ffabb-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="ffabb-296">Supprimer tous les temps d’exécution `3.0.0-preview6-27804-01` .NET Core sauf la version sans nécessiter la confirmation Y/N:</span><span class="sxs-lookup"><span data-stu-id="ffabb-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="ffabb-297">Supprimer tous les SDK .NET Core 1.1 sans avoir besoin d’une confirmation Y/n :</span><span class="sxs-lookup"><span data-stu-id="ffabb-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="ffabb-298">Supprimer le .NET Core 1.1.11 SDK sans sortie console:</span><span class="sxs-lookup"><span data-stu-id="ffabb-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="ffabb-299">Supprimer tous les SDK de base .NET qui peuvent être retirés en toute sécurité par cet outil :</span><span class="sxs-lookup"><span data-stu-id="ffabb-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="ffabb-300">Supprimer tous les SDK de base .NET qui peuvent être supprimés par cet outil, y compris les SDK qui peuvent être requis par Visual Studio (non recommandé) :</span><span class="sxs-lookup"><span data-stu-id="ffabb-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="ffabb-301">Supprimer tous les SDK core .NET qui sont spécifiés dans le fichier de réponse`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="ffabb-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="ffabb-302">Le contenu de *versions.rsp* est le suivant:</span><span class="sxs-lookup"><span data-stu-id="ffabb-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="ffabb-303">Étape 4 - Supprimer le dossier de repli NuGet (facultatif)</span><span class="sxs-lookup"><span data-stu-id="ffabb-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="ffabb-304">Dans certains cas, vous `NuGetFallbackFolder` n’avez plus besoin de la et peut vouloir le supprimer.</span><span class="sxs-lookup"><span data-stu-id="ffabb-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="ffabb-305">Pour plus d’informations sur la suppression de ce dossier, voir [Supprimer le NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="ffabb-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="ffabb-306">Désinstaller l’outil</span><span class="sxs-lookup"><span data-stu-id="ffabb-306">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="ffabb-307">Windows</span><span class="sxs-lookup"><span data-stu-id="ffabb-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="ffabb-308">Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="ffabb-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="ffabb-309">Recherchez `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="ffabb-310">Sélectionner **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="ffabb-310">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ffabb-311">macOS</span><span class="sxs-lookup"><span data-stu-id="ffabb-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="ffabb-312">Supprimer le fichier *dotnet-core-uninstall.tar.gz* téléchargé de l’annuaire où il a été installé.</span><span class="sxs-lookup"><span data-stu-id="ffabb-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="ffabb-313">Si vous avez décompressé le contenu de ce fichier dans un autre répertoire, assurez-vous de supprimer ce contenu ainsi.</span><span class="sxs-lookup"><span data-stu-id="ffabb-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
