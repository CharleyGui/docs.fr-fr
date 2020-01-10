---
title: Outil de désinstallation
description: Vue d’ensemble de l’outil de désinstallation de .NET Core, outil guidé qui permet le nettoyage contrôlé des kits de développement logiciel (SDK) .NET Core et des runtimes.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714550"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="a03a0-103">Outil de désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="a03a0-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="a03a0-104">L' [outil de désinstallation de .net Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) vous permet de supprimer des kits de développement logiciel (SDK) .net Core et des runtimes d’un système.</span><span class="sxs-lookup"><span data-stu-id="a03a0-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="a03a0-105">Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="a03a0-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="a03a0-106">L’outil prend en charge Windows et macOS.</span><span class="sxs-lookup"><span data-stu-id="a03a0-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="a03a0-107">Pour le moment, Linux n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a03a0-107">Linux is currently not supported.</span></span>

<span data-ttu-id="a03a0-108">Sur Windows, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes qui ont été installés à l’aide de l’un des programmes d’installation suivants :</span><span class="sxs-lookup"><span data-stu-id="a03a0-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="a03a0-109">Kit SDK .NET Core et le programme d’installation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a03a0-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="a03a0-110">Le programme d’installation de Visual Studio dans les versions antérieures à Visual Studio 2019 version 16,3.</span><span class="sxs-lookup"><span data-stu-id="a03a0-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="a03a0-111">Sur macOS, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes situés dans le dossier */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="a03a0-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="a03a0-112">En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les kits de développement logiciel (SDK) .NET Core et les runtimes sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a03a0-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="a03a0-113">Vous pouvez utiliser la commande `dotnet --info` pour rechercher tous les kits de développement logiciel (SDK) .NET Core et les runtimes installés, y compris les kits de développement logiciel (SDK) et runtimes que cet outil ne peut pas supprimer.</span><span class="sxs-lookup"><span data-stu-id="a03a0-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="a03a0-114">La commande `dotnet-core-uninstall list` affiche les kits de développement logiciel (SDK) qui peuvent être désinstallés avec l’outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="a03a0-115">Installer l’outil</span><span class="sxs-lookup"><span data-stu-id="a03a0-115">Install the tool</span></span>

<span data-ttu-id="a03a0-116">Vous pouvez télécharger l’outil de désinstallation de .NET Core à partir du dépôt github [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab/releases) .</span><span class="sxs-lookup"><span data-stu-id="a03a0-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="a03a0-117">L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="a03a0-118">Par conséquent, il doit être installé dans un répertoire protégé en écriture, tel que *C:\Program Files* sur Windows ou */usr/local/bin* sur MacOS.</span><span class="sxs-lookup"><span data-stu-id="a03a0-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="a03a0-119">Consultez également [l’accès avec élévation de privilèges pour les commandes dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="a03a0-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="a03a0-120">Des instructions d’installation détaillées sont disponibles sur la [page des versions de GitHub](https://github.com/dotnet/cli-lab/releases).</span><span class="sxs-lookup"><span data-stu-id="a03a0-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="a03a0-121">Exécution de l'outil</span><span class="sxs-lookup"><span data-stu-id="a03a0-121">Run the tool</span></span>

<span data-ttu-id="a03a0-122">Les étapes suivantes illustrent l’approche recommandée pour l’exécution de l’outil de désinstallation :</span><span class="sxs-lookup"><span data-stu-id="a03a0-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="a03a0-123">Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes</span><span class="sxs-lookup"><span data-stu-id="a03a0-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="a03a0-124">Étape 2 : effectuer une exécution à sec</span><span class="sxs-lookup"><span data-stu-id="a03a0-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="a03a0-125">Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core</span><span class="sxs-lookup"><span data-stu-id="a03a0-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="a03a0-126">Étape 4 : supprimer le dossier NuGet Fallback (facultatif)</span><span class="sxs-lookup"><span data-stu-id="a03a0-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="a03a0-127">Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes</span><span class="sxs-lookup"><span data-stu-id="a03a0-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="a03a0-128">La commande `dotnet-core-uninstall list` répertorie les kits de développement logiciel (SDK) .NET Core installés et les runtimes qui peuvent être supprimés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="a03a0-129">Certains kits de développement logiciel (SDK) et runtimes peuvent être requis par Visual Studio et ils s’affichent avec la raison pour laquelle il n’est pas recommandé de les désinstaller.</span><span class="sxs-lookup"><span data-stu-id="a03a0-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="a03a0-130">**dotnet-Core-liste de désinstallation**</span><span class="sxs-lookup"><span data-stu-id="a03a0-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="a03a0-131">Résumé</span><span class="sxs-lookup"><span data-stu-id="a03a0-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="a03a0-132">Options</span><span class="sxs-lookup"><span data-stu-id="a03a0-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="a03a0-133">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="a03a0-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="a03a0-134">Répertorie tous les runtimes ASP.NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="a03a0-135">Répertorie tous les groupes d’hébergement et Runtime .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="a03a0-136">Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-137">Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-138">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-138">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-140">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="a03a0-141">Répertorie tous les kits de développement logiciel (SDK) .NET Core x64 et les runtimes qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="a03a0-142">Répertorie tous les kits de développement logiciel (SDK) .NET Core x86 et les runtimes qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="a03a0-143">macOS</span><span class="sxs-lookup"><span data-stu-id="a03a0-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="a03a0-144">Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-145">Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="a03a0-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-146">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-146">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-147">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-148">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="a03a0-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="a03a0-149">Examples</span></span>

* <span data-ttu-id="a03a0-150">Répertorie tous les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être supprimés à l’aide de cet outil :</span><span class="sxs-lookup"><span data-stu-id="a03a0-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="a03a0-151">Répertoriez tous les kits de développement logiciel (SDK) et runtimes x64 .NET Core :</span><span class="sxs-lookup"><span data-stu-id="a03a0-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="a03a0-152">Répertorier tous les kits de développement logiciel (SDK) .NET Core x86 :</span><span class="sxs-lookup"><span data-stu-id="a03a0-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="a03a0-153">Étape 2 : effectuer une exécution à sec</span><span class="sxs-lookup"><span data-stu-id="a03a0-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="a03a0-154">Les commandes `dotnet-core-uninstall dry-run` et `dotnet-core-uninstall whatif` affichent les kits de développement logiciel (SDK) .NET Core et les runtimes qui seront supprimés en fonction des options fournies sans effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="a03a0-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="a03a0-155">Ces commandes sont des synonymes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-155">These commands are synonyms.</span></span>

<span data-ttu-id="a03a0-156">**dotnet-Core-désinstaller Dry-Run et DOTNET-Core-Uninstall WhatIf**</span><span class="sxs-lookup"><span data-stu-id="a03a0-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="a03a0-157">Résumé</span><span class="sxs-lookup"><span data-stu-id="a03a0-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="a03a0-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="a03a0-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="a03a0-159">Version spécifiée à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="a03a0-159">The specified version to uninstall.</span></span> <span data-ttu-id="a03a0-160">Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="a03a0-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="a03a0-161">Les fichiers réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a03a0-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="a03a0-162">Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a03a0-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="a03a0-163">Il s’agit de fichiers texte, généralement avec une extension \*. rsp, et chaque version est indiquée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="a03a0-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="a03a0-164">Pour spécifier un fichier réponse pour l’argument `VERSION`, utilisez le caractère \@ immédiatement suivi du nom du fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="a03a0-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="a03a0-165">Options</span><span class="sxs-lookup"><span data-stu-id="a03a0-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="a03a0-166">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="a03a0-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="a03a0-167">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="a03a0-168">Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="a03a0-169">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="a03a0-170">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a03a0-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="a03a0-171">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a03a0-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="a03a0-172">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="a03a0-173">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="a03a0-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="a03a0-174">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="a03a0-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="a03a0-175">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="a03a0-176">Supprime ASP.NET Core runtimes uniquement.</span><span class="sxs-lookup"><span data-stu-id="a03a0-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="a03a0-177">Supprime uniquement le Runtime .NET Core et les regroupements d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a03a0-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="a03a0-178">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la version de `major.minor` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="a03a0-179">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-180">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-181">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-181">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-182">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-183">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="a03a0-184">Doit être utilisé avec `--sdk`, `--runtime`et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.</span><span class="sxs-lookup"><span data-stu-id="a03a0-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="a03a0-185">Doit être utilisé avec `--sdk`, `--runtime`et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.</span><span class="sxs-lookup"><span data-stu-id="a03a0-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="a03a0-186">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a03a0-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="a03a0-187">Remarques :</span><span class="sxs-lookup"><span data-stu-id="a03a0-187">Notes:</span></span>

1. <span data-ttu-id="a03a0-188">Une seule des `--sdk`, `--runtime`, `--aspnet-runtime`et `--hosting-bundle` est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a03a0-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="a03a0-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="a03a0-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="a03a0-190">Si `--x64` ou `--x86` ne sont pas spécifiés, les paramètres x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="a03a0-191">macOS</span><span class="sxs-lookup"><span data-stu-id="a03a0-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="a03a0-192">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="a03a0-193">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="a03a0-194">La version spécifiée est conservée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="a03a0-195">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a03a0-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="a03a0-196">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a03a0-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="a03a0-197">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="a03a0-198">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="a03a0-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="a03a0-199">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="a03a0-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="a03a0-200">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="a03a0-201">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la version de `major.minor` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="a03a0-202">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-203">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-204">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-204">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-205">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-206">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="a03a0-207">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="a03a0-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="a03a0-208">Remarques :</span><span class="sxs-lookup"><span data-stu-id="a03a0-208">Notes:</span></span>

1. <span data-ttu-id="a03a0-209">Une seule des `--sdk` et `--runtime` est requise.</span><span class="sxs-lookup"><span data-stu-id="a03a0-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="a03a0-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="a03a0-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="a03a0-211">Exemples</span><span class="sxs-lookup"><span data-stu-id="a03a0-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="a03a0-212">Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK) ne sont pas inclus dans `dotnet-core-uninstall dry-run` sortie.</span><span class="sxs-lookup"><span data-stu-id="a03a0-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="a03a0-213">Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent ne pas être inclus dans la sortie, en fonction de l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a03a0-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="a03a0-214">Pour inclure tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l’option `--force`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="a03a0-215">Exécution à sec de la suppression de tous les runtimes .NET Core qui ont été remplacés par des correctifs plus élevés :</span><span class="sxs-lookup"><span data-stu-id="a03a0-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="a03a0-216">Exécution à sec de la suppression de tous les kits de développement logiciel (SDK) .NET Core sous la version `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="a03a0-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="a03a0-217">Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core</span><span class="sxs-lookup"><span data-stu-id="a03a0-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="a03a0-218">`dotnet-core-uninstall remove` désinstalle les kits de développement logiciel (SDK) .NET Core et les runtimes spécifiés par une collection d’options.</span><span class="sxs-lookup"><span data-stu-id="a03a0-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="a03a0-219">L’outil ne peut pas être utilisé pour désinstaller des kits de développement logiciel (SDK) et des runtimes avec la version 5,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a03a0-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="a03a0-220">Étant donné que cet outil a un comportement destructif, il est **fortement** recommandé d’effectuer une exécution à sec avant d’exécuter la commande Remove.</span><span class="sxs-lookup"><span data-stu-id="a03a0-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="a03a0-221">La série à sec vous montrera les kits de développement logiciel (SDK) .NET Core et les runtimes qui seront supprimés lorsque vous utiliserez la commande `remove`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="a03a0-222">Reportez-vous à [la rubrique dois-je supprimer une version ?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDK et runtimes peuvent être supprimés en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="a03a0-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="a03a0-223">Rappelez-vous des avertissements suivants :</span><span class="sxs-lookup"><span data-stu-id="a03a0-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="a03a0-224">Cet outil peut désinstaller les versions des kit SDK .NET Core requises par les fichiers `global.json` sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a03a0-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="a03a0-225">Vous pouvez réinstaller les kits de développement logiciel (SDK) .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="a03a0-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="a03a0-226">Cet outil peut désinstaller des versions du Runtime .NET Core qui sont requises par les applications dépendantes du Framework sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a03a0-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="a03a0-227">Vous pouvez réinstaller les runtimes .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="a03a0-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="a03a0-228">Cet outil peut désinstaller des versions du kit SDK .NET Core et du Runtime sur lesquelles s’appuie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a03a0-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="a03a0-229">Si vous interrompez votre installation de Visual Studio, exécutez « réparer » dans le programme d’installation de Visual Studio pour revenir à un état de travail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="a03a0-230">Par défaut, toutes les commandes conservent les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="a03a0-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="a03a0-231">Ces kits de développement logiciel (SDK) et runtimes peuvent être désinstallés en les répertoriant explicitement comme arguments ou à l’aide de l’option `--force`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="a03a0-232">L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="a03a0-233">Exécutez l’outil dans une invite de commandes d’administrateur sur Windows et avec `sudo` sur macOS.</span><span class="sxs-lookup"><span data-stu-id="a03a0-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="a03a0-234">Les commandes `dry-run` et `whatif` ne nécessitent pas d’élévation.</span><span class="sxs-lookup"><span data-stu-id="a03a0-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="a03a0-235">**dotnet-Core-désinstaller supprimer**</span><span class="sxs-lookup"><span data-stu-id="a03a0-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="a03a0-236">Résumé</span><span class="sxs-lookup"><span data-stu-id="a03a0-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="a03a0-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="a03a0-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="a03a0-238">Version spécifiée à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="a03a0-238">The specified version to uninstall.</span></span> <span data-ttu-id="a03a0-239">Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="a03a0-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="a03a0-240">Les fichiers réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a03a0-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="a03a0-241">Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a03a0-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="a03a0-242">Il s’agit de fichiers texte, généralement avec une extension \*. rsp, et chaque version est indiquée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="a03a0-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="a03a0-243">Pour spécifier un fichier réponse pour l’argument `VERSION`, utilisez le caractère \@ immédiatement suivi du nom du fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="a03a0-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="a03a0-244">Options</span><span class="sxs-lookup"><span data-stu-id="a03a0-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="a03a0-245">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="a03a0-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="a03a0-246">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="a03a0-247">Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="a03a0-248">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="a03a0-249">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a03a0-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="a03a0-250">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a03a0-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="a03a0-251">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="a03a0-252">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="a03a0-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="a03a0-253">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="a03a0-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="a03a0-254">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="a03a0-255">Supprime ASP.NET Core runtimes uniquement.</span><span class="sxs-lookup"><span data-stu-id="a03a0-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="a03a0-256">Supprime uniquement le Runtime .NET Core et les regroupements d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a03a0-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="a03a0-257">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la version de `major.minor` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="a03a0-258">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-259">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-260">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-260">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-261">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-262">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="a03a0-263">Doit être utilisé avec `--sdk`, `--runtime`et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.</span><span class="sxs-lookup"><span data-stu-id="a03a0-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="a03a0-264">Doit être utilisé avec `--sdk`, `--runtime`et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.</span><span class="sxs-lookup"><span data-stu-id="a03a0-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="a03a0-265">**`-y, --yes`** Exécute la commande sans demander de confirmation oui ou non.</span><span class="sxs-lookup"><span data-stu-id="a03a0-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="a03a0-266">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a03a0-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="a03a0-267">Remarques :</span><span class="sxs-lookup"><span data-stu-id="a03a0-267">Notes:</span></span>

1. <span data-ttu-id="a03a0-268">Une seule des `--sdk`, `--runtime`, `--aspnet-runtime`et `--hosting-bundle` est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a03a0-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="a03a0-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="a03a0-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="a03a0-270">Si `--x64` ou `--x86` ne sont pas spécifiés, les paramètres x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="a03a0-271">macOS</span><span class="sxs-lookup"><span data-stu-id="a03a0-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="a03a0-272">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="a03a0-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="a03a0-273">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="a03a0-274">La version spécifiée est conservée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="a03a0-275">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a03a0-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="a03a0-276">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a03a0-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="a03a0-277">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="a03a0-278">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="a03a0-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="a03a0-279">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="a03a0-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="a03a0-280">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="a03a0-281">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la version de `major.minor` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a03a0-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="a03a0-282">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="a03a0-283">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a03a0-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="a03a0-284">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="a03a0-284">Sets the verbosity level.</span></span> <span data-ttu-id="a03a0-285">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a03a0-286">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-286">The default value is `normal`.</span></span>

* <span data-ttu-id="a03a0-287">**`-y, --yes`** Exécute la commande sans demander de confirmation Y/N.</span><span class="sxs-lookup"><span data-stu-id="a03a0-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="a03a0-288">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="a03a0-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="a03a0-289">Remarques :</span><span class="sxs-lookup"><span data-stu-id="a03a0-289">Notes:</span></span>

1. <span data-ttu-id="a03a0-290">Une seule des `--sdk` et `--runtime` est requise.</span><span class="sxs-lookup"><span data-stu-id="a03a0-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="a03a0-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="a03a0-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="a03a0-292">Exemples</span><span class="sxs-lookup"><span data-stu-id="a03a0-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="a03a0-293">Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK) sont conservés.</span><span class="sxs-lookup"><span data-stu-id="a03a0-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="a03a0-294">Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent être conservés, en fonction de l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a03a0-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="a03a0-295">Pour supprimer tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l’option `--force`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="a03a0-296">Supprimez tous les runtimes .NET Core à l’exception de la `3.0.0-preview6-27804-01` de version sans demander de confirmation Y/N :</span><span class="sxs-lookup"><span data-stu-id="a03a0-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="a03a0-297">Supprimer tous les kits de développement logiciel (SDK) .NET Core 1,1 sans demander de confirmation Y/n :</span><span class="sxs-lookup"><span data-stu-id="a03a0-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="a03a0-298">Supprimez le kit de développement logiciel (SDK) .NET Core 1.1.11 au minimum sans sortie de la console :</span><span class="sxs-lookup"><span data-stu-id="a03a0-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="a03a0-299">Supprimez tous les kits de développement logiciel (SDK) .NET Core pouvant être supprimés en toute sécurité par cet outil :</span><span class="sxs-lookup"><span data-stu-id="a03a0-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="a03a0-300">Supprimer tous les kits de développement logiciel (SDK) .NET Core qui peuvent être supprimés par cet outil, y compris les kits de développement logiciel (SDK) qui peuvent être requis par Visual Studio (non recommandé) :</span><span class="sxs-lookup"><span data-stu-id="a03a0-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="a03a0-301">Supprimez tous les kits de développement logiciel (SDK) .NET Core spécifiés dans le fichier réponse `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="a03a0-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="a03a0-302">Le contenu de *versions. rsp* est le suivant :</span><span class="sxs-lookup"><span data-stu-id="a03a0-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="a03a0-303">Étape 4 : supprimer le dossier NuGet Fallback (facultatif)</span><span class="sxs-lookup"><span data-stu-id="a03a0-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="a03a0-304">Dans certains cas, vous n’avez plus besoin de la `NuGetFallbackFolder` et vous souhaiterez peut-être la supprimer.</span><span class="sxs-lookup"><span data-stu-id="a03a0-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="a03a0-305">Pour plus d’informations sur la suppression de ce dossier, consultez [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="a03a0-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="a03a0-306">Désinstaller l’outil</span><span class="sxs-lookup"><span data-stu-id="a03a0-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="a03a0-307">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="a03a0-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="a03a0-308">Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="a03a0-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="a03a0-309">Recherchez `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="a03a0-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="a03a0-310">Sélectionnez **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="a03a0-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="a03a0-311">macOS</span><span class="sxs-lookup"><span data-stu-id="a03a0-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="a03a0-312">Supprimez le fichier *dotnet-Core-Uninstall. tar. gz* téléchargé à partir du répertoire où il a été installé.</span><span class="sxs-lookup"><span data-stu-id="a03a0-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="a03a0-313">Si vous dézippéz le contenu de ce fichier dans un autre répertoire, veillez à supprimer également ce contenu.</span><span class="sxs-lookup"><span data-stu-id="a03a0-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
