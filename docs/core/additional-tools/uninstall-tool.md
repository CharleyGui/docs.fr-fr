---
title: Outil désinstaller
description: Un aperçu de l’outil .NET Core Uninstall, un outil guidé qui permet le nettoyage contrôlé des SDKs et des runtimes .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507319"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="b2386-103">Outil de désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2386-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="b2386-104">[L’outil .NET Core Uninstall](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) vous permet de supprimer .NET Core SDKs et Runtimes d’un système.</span><span class="sxs-lookup"><span data-stu-id="b2386-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="b2386-105">Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="b2386-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="b2386-106">L’outil prend en charge Windows et macOS.</span><span class="sxs-lookup"><span data-stu-id="b2386-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="b2386-107">Pour le moment, Linux n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b2386-107">Linux is currently not supported.</span></span>

<span data-ttu-id="b2386-108">Sur Windows, l’outil ne peut désinstaller les SDK et les Runtimes qui ont été installés à l’aide d’un des installateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="b2386-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="b2386-109">Le .NET Core SDK et l’installateur de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2386-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="b2386-110">L’installateur Visual Studio en versions antérieures à la version 16.3 de Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="b2386-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="b2386-111">Sur macOS, l’outil ne peut désinstaller les SDK et les temps d’exécution situés dans le dossier */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="b2386-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="b2386-112">En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les SDKs de base .NET et les temps d’exécution sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="b2386-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="b2386-113">Vous pouvez `dotnet --info` utiliser la commande pour trouver tous les SDKs de base .NET et les temps d’exécution installés, y compris les SDK et les temps d’exécution que cet outil ne peut pas supprimer.</span><span class="sxs-lookup"><span data-stu-id="b2386-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="b2386-114">La `dotnet-core-uninstall list` commande affiche quels SDKs peuvent être désinstallés avec l’outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="b2386-115">Installer l’outil</span><span class="sxs-lookup"><span data-stu-id="b2386-115">Install the tool</span></span>

<span data-ttu-id="b2386-116">Vous pouvez télécharger l’outil .NET Core Uninstall à partir [d’ici](https://aka.ms/dotnet-core-uninstall-tool) et trouver le code source au référentiel [GitHub dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="b2386-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="b2386-117">L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2386-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b2386-118">Par conséquent, il devrait être installé dans un répertoire protégé par l’écriture tels que *les fichiers de programme C: 'program* sur Windows ou */usr/local/bin* sur macOS.</span><span class="sxs-lookup"><span data-stu-id="b2386-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="b2386-119">Voir aussi [Accès élevé pour les commandes dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="b2386-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="b2386-120">Pour plus d’informations, voir les [instructions d’installation détaillées](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="b2386-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="b2386-121">Exécuter l’outil</span><span class="sxs-lookup"><span data-stu-id="b2386-121">Run the tool</span></span>

<span data-ttu-id="b2386-122">Les étapes suivantes montrent l’approche recommandée pour l’exécution de l’outil de désinstallation :</span><span class="sxs-lookup"><span data-stu-id="b2386-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="b2386-123">Étape 1 - Affichage installé .NET Core SDKs et runtimes</span><span class="sxs-lookup"><span data-stu-id="b2386-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b2386-124">Étape 2 - Faire une course à sec</span><span class="sxs-lookup"><span data-stu-id="b2386-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="b2386-125">Étape 3 - Uninstall .NET Core SDKs and Runtimes</span><span class="sxs-lookup"><span data-stu-id="b2386-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b2386-126">Étape 4 - Supprimer le dossier de repli NuGet (facultatif)</span><span class="sxs-lookup"><span data-stu-id="b2386-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="b2386-127">Étape 1 - Affichage installé .NET Core SDKs et runtimes</span><span class="sxs-lookup"><span data-stu-id="b2386-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="b2386-128">La `dotnet-core-uninstall list` commande répertorie les SDKs et les temps d’exécution .NET core installés qui peuvent être supprimés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="b2386-129">Certains SDK et les durées d’exécution peuvent être nécessaires par Visual Studio et ils sont affichés avec une note de pourquoi il n’est pas recommandé de les désinstaller.</span><span class="sxs-lookup"><span data-stu-id="b2386-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="b2386-130">La sortie `dotnet-core-uninstall list` de la commande ne correspondra pas à `dotnet --info` la liste des versions installées dans la sortie de dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="b2386-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="b2386-131">Plus précisément, cet outil n’affichera pas les versions installées par des fichiers zip ou gérées par Visual Studio (toute version installée avec Visual Studio 2019 16.3 ou plus tard).</span><span class="sxs-lookup"><span data-stu-id="b2386-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="b2386-132">Une façon de vérifier si une version est gérée `Add or Remove Programs`par Visual Studio est de la voir dans , où Visual Studio versions gérées sont marqués comme tels dans leurs noms d’affichage.</span><span class="sxs-lookup"><span data-stu-id="b2386-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="b2386-133">**liste dotnet-core-uninstall**</span><span class="sxs-lookup"><span data-stu-id="b2386-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2386-134">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b2386-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="b2386-135">Options</span><span class="sxs-lookup"><span data-stu-id="b2386-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2386-136">Windows</span><span class="sxs-lookup"><span data-stu-id="b2386-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="b2386-137">Répertorie tous les temps d’exécution ASP.NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2386-138">Répertorie tous les forfaits .NET Core et les forfaits d’hébergement qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2386-139">Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-140">Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-141">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-141">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-142">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-143">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2386-144">Répertorie tous les SDKs et les runtimes de base x64 .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="b2386-145">Répertorie tous les SDKs et les runtimes de base x86 .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2386-146">macOS</span><span class="sxs-lookup"><span data-stu-id="b2386-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="b2386-147">Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-148">Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="b2386-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-149">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-149">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-150">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-151">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="b2386-152">Exemples</span><span class="sxs-lookup"><span data-stu-id="b2386-152">Examples</span></span>

* <span data-ttu-id="b2386-153">Énumérez tous les SDKs de base de .NET et les temps d’exécution qui peuvent être supprimés avec cet outil :</span><span class="sxs-lookup"><span data-stu-id="b2386-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="b2386-154">Liste tous les X64 .NET Core SDKs et runtimes:</span><span class="sxs-lookup"><span data-stu-id="b2386-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="b2386-155">Liste tous les X86 .NET Core SDKs:</span><span class="sxs-lookup"><span data-stu-id="b2386-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="b2386-156">Étape 2 - Faire une course à sec</span><span class="sxs-lookup"><span data-stu-id="b2386-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="b2386-157">Les `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` commandes et les commandes affichent les SDKs et les temps d’exécution .NET Core qui seront supprimés en fonction des options fournies sans effectuer le désinstallation.</span><span class="sxs-lookup"><span data-stu-id="b2386-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="b2386-158">Ces commandes sont synonymes.</span><span class="sxs-lookup"><span data-stu-id="b2386-158">These commands are synonyms.</span></span>

<span data-ttu-id="b2386-159">**dotnet-core-uninstall dry-run et dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="b2386-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2386-160">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b2386-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b2386-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="b2386-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b2386-162">La version spécifiée pour désinstaller.</span><span class="sxs-lookup"><span data-stu-id="b2386-162">The specified version to uninstall.</span></span> <span data-ttu-id="b2386-163">Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="b2386-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b2386-164">Les fichiers de réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b2386-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b2386-165">Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b2386-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b2386-166">Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.</span><span class="sxs-lookup"><span data-stu-id="b2386-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b2386-167">Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.</span><span class="sxs-lookup"><span data-stu-id="b2386-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b2386-168">Options</span><span class="sxs-lookup"><span data-stu-id="b2386-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2386-169">Windows</span><span class="sxs-lookup"><span data-stu-id="b2386-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b2386-170">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2386-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2386-171">Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b2386-172">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="b2386-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2386-173">Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b2386-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2386-174">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="b2386-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2386-175">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="b2386-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2386-176">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="b2386-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2386-177">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="b2386-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2386-178">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="b2386-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b2386-179">Supprime ASP.NET les temps d’exécution Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2386-180">Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2386-181">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2386-182">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-183">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-184">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-184">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-185">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-186">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2386-187">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2386-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b2386-188">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2386-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b2386-189">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2386-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b2386-190">Remarques :</span><span class="sxs-lookup"><span data-stu-id="b2386-190">Notes:</span></span>

1. <span data-ttu-id="b2386-191">Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2386-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b2386-192">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="b2386-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b2386-193">Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="b2386-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2386-194">macOS</span><span class="sxs-lookup"><span data-stu-id="b2386-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b2386-195">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2386-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2386-196">Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b2386-197">La version spécifiée restera.</span><span class="sxs-lookup"><span data-stu-id="b2386-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2386-198">Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b2386-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2386-199">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="b2386-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2386-200">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="b2386-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2386-201">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="b2386-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2386-202">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="b2386-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2386-203">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="b2386-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2386-204">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2386-205">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-206">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-207">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-207">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-208">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-209">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="b2386-210">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="b2386-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b2386-211">Remarques :</span><span class="sxs-lookup"><span data-stu-id="b2386-211">Notes:</span></span>

1. <span data-ttu-id="b2386-212">Exactement un `--sdk` `--runtime` de et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2386-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b2386-213">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="b2386-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b2386-214">Exemples</span><span class="sxs-lookup"><span data-stu-id="b2386-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b2386-215">Par défaut, les SDKs de base .NET et les temps d’exécution qui `dotnet-core-uninstall dry-run` peuvent être exigés par Visual Studio ou d’autres SDK ne sont pas inclus dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="b2386-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="b2386-216">Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent ne pas être inclus dans la sortie, selon l’état de la machine.</span><span class="sxs-lookup"><span data-stu-id="b2386-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="b2386-217">Pour inclure tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`</span><span class="sxs-lookup"><span data-stu-id="b2386-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b2386-218">Course sèche de l’élimination de tous les temps d’exécution .NET Core qui ont été remplacés par des correctifs plus élevés:</span><span class="sxs-lookup"><span data-stu-id="b2386-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="b2386-219">Course sèche de la suppression de tous les `2.2.301`SDKs .NET Core en dessous de la version :</span><span class="sxs-lookup"><span data-stu-id="b2386-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="b2386-220">Étape 3 - Uninstall .NET Core SDKs and Runtimes</span><span class="sxs-lookup"><span data-stu-id="b2386-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="b2386-221">`dotnet-core-uninstall remove`désinstaller .NET Core SDKs et Runtimes qui sont spécifiés par une collection d’options.</span><span class="sxs-lookup"><span data-stu-id="b2386-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="b2386-222">L’outil ne peut pas être utilisé pour désinstaller les SDK et les Runtimes avec la version 5.0 ou plus.</span><span class="sxs-lookup"><span data-stu-id="b2386-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="b2386-223">Depuis cet outil a un comportement destructeur, il est **fortement** recommandé que vous faites une course à sec avant d’exécuter la commande de suppression.</span><span class="sxs-lookup"><span data-stu-id="b2386-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="b2386-224">La course à sec vous montrera ce que les SDKs de `remove` base de .NET et les temps d’exécution seront supprimés lorsque vous utilisez la commande.</span><span class="sxs-lookup"><span data-stu-id="b2386-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="b2386-225">Se référer à [Dois-je supprimer une version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDKs et runtimes sont sûrs à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b2386-225">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="b2386-226">Rappelez-vous des avertissements suivants :</span><span class="sxs-lookup"><span data-stu-id="b2386-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="b2386-227">Cet outil peut désinstaller les versions du SDK `global.json` .NET Core qui sont requis par les fichiers sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="b2386-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="b2386-228">Vous pouvez réinstaller .NET Core SDKs à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="b2386-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b2386-229">Cet outil peut désinstaller les versions du temps d’exécution .NET Core qui sont requis par des applications dépendantes du cadre de votre machine.</span><span class="sxs-lookup"><span data-stu-id="b2386-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="b2386-230">Vous pouvez réinstaller les temps d’exécution .NET Core à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="b2386-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b2386-231">Cet outil peut désinstaller les versions du .NET Core SDK et le temps d’exécution sur lequel Visual Studio s’appuie.</span><span class="sxs-lookup"><span data-stu-id="b2386-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="b2386-232">Si vous cassez votre installation Visual Studio, exécutez "Repair" dans l’installateur Visual Studio pour revenir à un état de travail.</span><span class="sxs-lookup"><span data-stu-id="b2386-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="b2386-233">Par défaut, toutes les commandes conservent les SDKs et les temps d’exécution .NET Core qui peuvent être requis par Visual Studio ou d’autres SDK.</span><span class="sxs-lookup"><span data-stu-id="b2386-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="b2386-234">Ces SDK et runtimes peuvent être désinstallés en `--force` les énumérant explicitement comme arguments ou en utilisant l’option.</span><span class="sxs-lookup"><span data-stu-id="b2386-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="b2386-235">L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2386-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b2386-236">Exécutez l’outil dans une invite `sudo` de commande d’administrateur sur Windows et avec sur macOS.</span><span class="sxs-lookup"><span data-stu-id="b2386-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="b2386-237">L’élévation `dry-run` et `whatif` les commandes ne nécessitent pas d’élévation.</span><span class="sxs-lookup"><span data-stu-id="b2386-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="b2386-238">**dotnet-core-uninstall supprimer**</span><span class="sxs-lookup"><span data-stu-id="b2386-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2386-239">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b2386-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b2386-240">Arguments</span><span class="sxs-lookup"><span data-stu-id="b2386-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b2386-241">La version spécifiée pour désinstaller.</span><span class="sxs-lookup"><span data-stu-id="b2386-241">The specified version to uninstall.</span></span> <span data-ttu-id="b2386-242">Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="b2386-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b2386-243">Les fichiers de réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b2386-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b2386-244">Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b2386-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b2386-245">Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.</span><span class="sxs-lookup"><span data-stu-id="b2386-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b2386-246">Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.</span><span class="sxs-lookup"><span data-stu-id="b2386-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b2386-247">Options</span><span class="sxs-lookup"><span data-stu-id="b2386-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2386-248">Windows</span><span class="sxs-lookup"><span data-stu-id="b2386-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b2386-249">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2386-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2386-250">Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b2386-251">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="b2386-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2386-252">Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b2386-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2386-253">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="b2386-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2386-254">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="b2386-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2386-255">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="b2386-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2386-256">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="b2386-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2386-257">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="b2386-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b2386-258">Supprime ASP.NET les temps d’exécution Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2386-259">Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2386-260">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2386-261">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-262">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-263">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-263">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-264">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-265">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2386-266">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2386-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b2386-267">Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2386-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b2386-268">**`-y, --yes`** Exécutez la commande sans nécessiter de confirmation oui ou non.</span><span class="sxs-lookup"><span data-stu-id="b2386-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="b2386-269">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2386-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b2386-270">Remarques :</span><span class="sxs-lookup"><span data-stu-id="b2386-270">Notes:</span></span>

1. <span data-ttu-id="b2386-271">Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2386-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b2386-272">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="b2386-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b2386-273">Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="b2386-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2386-274">macOS</span><span class="sxs-lookup"><span data-stu-id="b2386-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b2386-275">Supprime tous les SDKs et les temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2386-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2386-276">Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b2386-277">La version spécifiée restera.</span><span class="sxs-lookup"><span data-stu-id="b2386-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2386-278">Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b2386-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2386-279">Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="b2386-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2386-280">Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="b2386-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2386-281">Cette option protège global.json.</span><span class="sxs-lookup"><span data-stu-id="b2386-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2386-282">Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.</span><span class="sxs-lookup"><span data-stu-id="b2386-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2386-283">Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="b2386-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2386-284">Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2386-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2386-285">Supprime les temps d’exécution .NET Core seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2386-286">Supprime .NET Core SDKs seulement.</span><span class="sxs-lookup"><span data-stu-id="b2386-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2386-287">Définit le niveau de verbosité.</span><span class="sxs-lookup"><span data-stu-id="b2386-287">Sets the verbosity level.</span></span> <span data-ttu-id="b2386-288">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b2386-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2386-289">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2386-289">The default value is `normal`.</span></span>

* <span data-ttu-id="b2386-290">**`-y, --yes`** Exécutez la commande sans nécessiter la confirmation de Y/N.</span><span class="sxs-lookup"><span data-stu-id="b2386-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="b2386-291">**`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="b2386-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b2386-292">Remarques :</span><span class="sxs-lookup"><span data-stu-id="b2386-292">Notes:</span></span>

1. <span data-ttu-id="b2386-293">Exactement un `--sdk` `--runtime` de et est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2386-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b2386-294">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="b2386-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b2386-295">Exemples</span><span class="sxs-lookup"><span data-stu-id="b2386-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b2386-296">Par défaut, les SDK core .NET et les temps d’exécution qui peuvent être requis par Visual Studio ou d’autres SDK sont conservés.</span><span class="sxs-lookup"><span data-stu-id="b2386-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="b2386-297">Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent rester, selon l’état de la machine.</span><span class="sxs-lookup"><span data-stu-id="b2386-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="b2386-298">Pour supprimer tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`</span><span class="sxs-lookup"><span data-stu-id="b2386-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b2386-299">Supprimer tous les temps d’exécution `3.0.0-preview6-27804-01` .NET Core sauf la version sans nécessiter la confirmation Y/N:</span><span class="sxs-lookup"><span data-stu-id="b2386-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="b2386-300">Supprimer tous les SDK .NET Core 1.1 sans avoir besoin d’une confirmation Y/n :</span><span class="sxs-lookup"><span data-stu-id="b2386-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="b2386-301">Supprimer le .NET Core 1.1.11 SDK sans sortie console:</span><span class="sxs-lookup"><span data-stu-id="b2386-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="b2386-302">Supprimer tous les SDK de base .NET qui peuvent être retirés en toute sécurité par cet outil :</span><span class="sxs-lookup"><span data-stu-id="b2386-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="b2386-303">Supprimer tous les SDK de base .NET qui peuvent être supprimés par cet outil, y compris les SDK qui peuvent être requis par Visual Studio (non recommandé) :</span><span class="sxs-lookup"><span data-stu-id="b2386-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="b2386-304">Supprimer tous les SDK core .NET qui sont spécifiés dans le fichier de réponse`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="b2386-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="b2386-305">Le contenu de *versions.rsp* est le suivant:</span><span class="sxs-lookup"><span data-stu-id="b2386-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="b2386-306">Étape 4 - Supprimer le dossier de repli NuGet (facultatif)</span><span class="sxs-lookup"><span data-stu-id="b2386-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="b2386-307">Dans certains cas, vous `NuGetFallbackFolder` n’avez plus besoin de la et peut vouloir le supprimer.</span><span class="sxs-lookup"><span data-stu-id="b2386-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="b2386-308">Pour plus d’informations sur la suppression de ce dossier, voir [Supprimer le NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="b2386-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="b2386-309">Désinstaller l’outil</span><span class="sxs-lookup"><span data-stu-id="b2386-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2386-310">Windows</span><span class="sxs-lookup"><span data-stu-id="b2386-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="b2386-311">Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="b2386-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="b2386-312">Recherchez `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="b2386-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="b2386-313">Sélectionner **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="b2386-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2386-314">macOS</span><span class="sxs-lookup"><span data-stu-id="b2386-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="b2386-315">Supprimer le fichier *dotnet-core-uninstall.tar.gz* téléchargé de l’annuaire où il a été installé.</span><span class="sxs-lookup"><span data-stu-id="b2386-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="b2386-316">Si vous avez décompressé le contenu de ce fichier dans un autre répertoire, assurez-vous de supprimer ce contenu ainsi.</span><span class="sxs-lookup"><span data-stu-id="b2386-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
