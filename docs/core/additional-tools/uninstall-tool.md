---
title: Outil de désinstallation
description: Vue d’ensemble de l’outil de désinstallation de .NET Core, outil guidé qui permet le nettoyage contrôlé des kits de développement logiciel (SDK) .NET Core et des runtimes.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446904"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="2ea91-103">Outil de désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ea91-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="2ea91-104">L' [outil de désinstallation de .net Core](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ) vous permet de supprimer des kits de développement logiciel (SDK) .net Core et des runtimes d’un système.</span><span class="sxs-lookup"><span data-stu-id="2ea91-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="2ea91-105">Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ea91-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="2ea91-106">L’outil prend en charge Windows et macOS.</span><span class="sxs-lookup"><span data-stu-id="2ea91-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="2ea91-107">Pour le moment, Linux n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2ea91-107">Linux is currently not supported.</span></span>

<span data-ttu-id="2ea91-108">Sur Windows, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes qui ont été installés à l’aide de l’un des programmes d’installation suivants :</span><span class="sxs-lookup"><span data-stu-id="2ea91-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="2ea91-109">Kit SDK .NET Core et le programme d’installation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2ea91-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="2ea91-110">Le programme d’installation de Visual Studio dans les versions antérieures à Visual Studio 2019 version 16,3.</span><span class="sxs-lookup"><span data-stu-id="2ea91-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="2ea91-111">Sur macOS, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes situés dans le dossier */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="2ea91-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="2ea91-112">En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les kits de développement logiciel (SDK) .NET Core et les runtimes sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ea91-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="2ea91-113">Vous pouvez utiliser la `dotnet --info` commande pour rechercher tous les kits de développement logiciel (SDK) .net Core et les runtimes installés, y compris les kits de développement logiciel (SDK) et runtimes que cet outil ne peut pas supprimer.</span><span class="sxs-lookup"><span data-stu-id="2ea91-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="2ea91-114">La `dotnet-core-uninstall list` commande affiche les kits de développement logiciel (SDK) qui peuvent être désinstallés avec l’outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="2ea91-115">Installer l’outil</span><span class="sxs-lookup"><span data-stu-id="2ea91-115">Install the tool</span></span>

<span data-ttu-id="2ea91-116">Vous pouvez télécharger l’outil de désinstallation de .NET Core à partir d' [ici](https://aka.ms/dotnet-core-uninstall-tool) et rechercher le code source dans le référentiel GitHub [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab) .</span><span class="sxs-lookup"><span data-stu-id="2ea91-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="2ea91-117">L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="2ea91-118">Par conséquent, il doit être installé dans un répertoire protégé en écriture, tel que *C:\Program Files* sur Windows ou */usr/local/bin* sur MacOS.</span><span class="sxs-lookup"><span data-stu-id="2ea91-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="2ea91-119">Consultez également [l’accès avec élévation de privilèges pour les commandes dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="2ea91-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="2ea91-120">Pour plus d’informations, consultez les [instructions d’installation détaillées](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="2ea91-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="2ea91-121">Exécution de l'outil</span><span class="sxs-lookup"><span data-stu-id="2ea91-121">Run the tool</span></span>

<span data-ttu-id="2ea91-122">Les étapes suivantes illustrent l’approche recommandée pour l’exécution de l’outil de désinstallation :</span><span class="sxs-lookup"><span data-stu-id="2ea91-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="2ea91-123">Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes</span><span class="sxs-lookup"><span data-stu-id="2ea91-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="2ea91-124">Étape 2 : effectuer une exécution à sec</span><span class="sxs-lookup"><span data-stu-id="2ea91-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="2ea91-125">Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ea91-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="2ea91-126">Étape 4 : supprimer le dossier NuGet Fallback (facultatif)</span><span class="sxs-lookup"><span data-stu-id="2ea91-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="2ea91-127">Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes</span><span class="sxs-lookup"><span data-stu-id="2ea91-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="2ea91-128">La `dotnet-core-uninstall list` commande répertorie les kits de développement logiciel (SDK) .net Core installés et les runtimes qui peuvent être supprimés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="2ea91-129">Certains kits de développement logiciel (SDK) et runtimes peuvent être requis par Visual Studio et ils s’affichent avec la raison pour laquelle il n’est pas recommandé de les désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ea91-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="2ea91-130">La sortie de la `dotnet-core-uninstall list` commande ne correspond pas à la liste des versions installées dans la sortie de `dotnet --info` dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="2ea91-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="2ea91-131">Plus précisément, cet outil n’affiche pas les versions installées par les fichiers zip ou gérées par Visual Studio (n’importe quelle version installée avec Visual Studio 2019 16,3 ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="2ea91-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="2ea91-132">Une façon de vérifier si une version est gérée par Visual Studio est de l’afficher dans `Add or Remove Programs` , où les versions gérées de Visual Studio sont marquées comme telles dans leurs noms complets.</span><span class="sxs-lookup"><span data-stu-id="2ea91-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="2ea91-133">**dotnet-Core-liste de désinstallation**</span><span class="sxs-lookup"><span data-stu-id="2ea91-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="2ea91-134">Synopsis</span><span class="sxs-lookup"><span data-stu-id="2ea91-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="2ea91-135">Options</span><span class="sxs-lookup"><span data-stu-id="2ea91-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="2ea91-136">Windows</span><span class="sxs-lookup"><span data-stu-id="2ea91-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="2ea91-137">Répertorie tous les runtimes ASP.NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="2ea91-138">Répertorie toutes les offres d’hébergement .NET Core qui peuvent être désinstallées avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="2ea91-139">Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-140">Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-141">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-141">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-142">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-143">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="2ea91-144">Répertorie tous les kits de développement logiciel (SDK) .NET Core x64 et les runtimes qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="2ea91-145">Répertorie tous les kits de développement logiciel (SDK) .NET Core x86 et les runtimes qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="2ea91-146">macOS</span><span class="sxs-lookup"><span data-stu-id="2ea91-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="2ea91-147">Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-148">Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.</span><span class="sxs-lookup"><span data-stu-id="2ea91-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-149">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-149">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-150">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-151">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="2ea91-152">Exemples</span><span class="sxs-lookup"><span data-stu-id="2ea91-152">Examples</span></span>

* <span data-ttu-id="2ea91-153">Répertorie tous les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être supprimés à l’aide de cet outil :</span><span class="sxs-lookup"><span data-stu-id="2ea91-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="2ea91-154">Répertoriez tous les kits de développement logiciel (SDK) et runtimes x64 .NET Core :</span><span class="sxs-lookup"><span data-stu-id="2ea91-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="2ea91-155">Répertorier tous les kits de développement logiciel (SDK) .NET Core x86 :</span><span class="sxs-lookup"><span data-stu-id="2ea91-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="2ea91-156">Étape 2 : effectuer une exécution à sec</span><span class="sxs-lookup"><span data-stu-id="2ea91-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="2ea91-157">Les `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` commandes et affichent les kits de développement logiciel (SDK) .net Core et les runtimes qui seront supprimés en fonction des options fournies sans effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="2ea91-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="2ea91-158">Ces commandes sont des synonymes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-158">These commands are synonyms.</span></span>

<span data-ttu-id="2ea91-159">**dotnet-Core-désinstaller Dry-Run et DOTNET-Core-Uninstall WhatIf**</span><span class="sxs-lookup"><span data-stu-id="2ea91-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="2ea91-160">Synopsis</span><span class="sxs-lookup"><span data-stu-id="2ea91-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="2ea91-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ea91-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="2ea91-162">Version spécifiée à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ea91-162">The specified version to uninstall.</span></span> <span data-ttu-id="2ea91-163">Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="2ea91-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="2ea91-164">Les fichiers réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2ea91-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="2ea91-165">Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2ea91-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="2ea91-166">Il s’agit de fichiers texte, généralement avec une \* extension. rsp, et chaque version est indiquée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="2ea91-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="2ea91-167">Pour spécifier un fichier réponse pour l' `VERSION` argument, utilisez le \@ caractère immédiatement suivi du nom du fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="2ea91-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="2ea91-168">Options</span><span class="sxs-lookup"><span data-stu-id="2ea91-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="2ea91-169">Windows</span><span class="sxs-lookup"><span data-stu-id="2ea91-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="2ea91-170">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-171">Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="2ea91-172">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-173">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2ea91-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="2ea91-174">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2ea91-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="2ea91-175">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="2ea91-176">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="2ea91-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="2ea91-177">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="2ea91-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="2ea91-178">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="2ea91-179">Supprime ASP.NET Core runtimes uniquement.</span><span class="sxs-lookup"><span data-stu-id="2ea91-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="2ea91-180">Supprime uniquement le Runtime .NET Core et les regroupements d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="2ea91-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="2ea91-181">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="2ea91-182">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-183">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-184">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-184">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-185">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-186">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="2ea91-187">Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.</span><span class="sxs-lookup"><span data-stu-id="2ea91-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="2ea91-188">Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.</span><span class="sxs-lookup"><span data-stu-id="2ea91-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="2ea91-189">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ea91-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="2ea91-190">Remarques :</span><span class="sxs-lookup"><span data-stu-id="2ea91-190">Notes:</span></span>

1. <span data-ttu-id="2ea91-191">Exactement l’un des `--sdk` ,, `--runtime` `--aspnet-runtime` et `--hosting-bundle` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2ea91-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="2ea91-192">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="2ea91-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="2ea91-193">Si `--x64` ou `--x86` n’est pas spécifié, les paramètres x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="2ea91-194">macOS</span><span class="sxs-lookup"><span data-stu-id="2ea91-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="2ea91-195">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-196">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="2ea91-197">La version spécifiée est conservée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-198">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2ea91-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="2ea91-199">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2ea91-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="2ea91-200">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="2ea91-201">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="2ea91-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="2ea91-202">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="2ea91-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="2ea91-203">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="2ea91-204">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="2ea91-205">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-206">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-207">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-207">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-208">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-209">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="2ea91-210">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="2ea91-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="2ea91-211">Remarques :</span><span class="sxs-lookup"><span data-stu-id="2ea91-211">Notes:</span></span>

1. <span data-ttu-id="2ea91-212">Une seule `--sdk` et unique `--runtime` est requise.</span><span class="sxs-lookup"><span data-stu-id="2ea91-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="2ea91-213">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="2ea91-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="2ea91-214">Exemples</span><span class="sxs-lookup"><span data-stu-id="2ea91-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="2ea91-215">Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres SDK ne sont pas inclus dans la `dotnet-core-uninstall dry-run` sortie.</span><span class="sxs-lookup"><span data-stu-id="2ea91-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="2ea91-216">Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent ne pas être inclus dans la sortie, en fonction de l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ea91-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="2ea91-217">Pour inclure tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l' `--force` option.</span><span class="sxs-lookup"><span data-stu-id="2ea91-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="2ea91-218">Exécution à sec de la suppression de tous les runtimes .NET Core qui ont été remplacés par des correctifs plus élevés :</span><span class="sxs-lookup"><span data-stu-id="2ea91-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="2ea91-219">Exécution à sec de la suppression de tous les kits de développement logiciel (SDK) .NET Core sous la version `2.2.301` :</span><span class="sxs-lookup"><span data-stu-id="2ea91-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="2ea91-220">Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ea91-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="2ea91-221">`dotnet-core-uninstall remove`désinstalle les kits de développement logiciel (SDK) .NET Core et les runtimes spécifiés par une collection d’options.</span><span class="sxs-lookup"><span data-stu-id="2ea91-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="2ea91-222">L’outil ne peut pas être utilisé pour désinstaller des kits de développement logiciel (SDK) et des runtimes avec la version 5,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2ea91-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="2ea91-223">Étant donné que cet outil a un comportement destructif, il est **fortement** recommandé d’effectuer une exécution à sec avant d’exécuter la commande Remove.</span><span class="sxs-lookup"><span data-stu-id="2ea91-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="2ea91-224">La série à sec vous montrera les kits de développement logiciel (SDK) .NET Core et les runtimes qui seront supprimés lorsque vous utiliserez la `remove` commande.</span><span class="sxs-lookup"><span data-stu-id="2ea91-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="2ea91-225">Reportez-vous à [la rubrique dois-je supprimer une version ?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDK et runtimes peuvent être supprimés en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="2ea91-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="2ea91-226">Rappelez-vous des avertissements suivants :</span><span class="sxs-lookup"><span data-stu-id="2ea91-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="2ea91-227">Cet outil peut désinstaller les versions des kit SDK .NET Core requises par les `global.json` fichiers sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ea91-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="2ea91-228">Vous pouvez réinstaller les kits de développement logiciel (SDK) .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="2ea91-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="2ea91-229">Cet outil peut désinstaller des versions du Runtime .NET Core qui sont requises par les applications dépendantes du Framework sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ea91-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="2ea91-230">Vous pouvez réinstaller les runtimes .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="2ea91-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="2ea91-231">Cet outil peut désinstaller des versions du kit SDK .NET Core et du Runtime sur lesquelles s’appuie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ea91-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="2ea91-232">Si vous interrompez votre installation de Visual Studio, exécutez « réparer » dans le programme d’installation de Visual Studio pour revenir à un état de travail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="2ea91-233">Par défaut, toutes les commandes conservent les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="2ea91-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="2ea91-234">Ces kits de développement logiciel (SDK) et runtimes peuvent être désinstallés en les répertoriant explicitement comme arguments ou à l’aide de l' `--force` option.</span><span class="sxs-lookup"><span data-stu-id="2ea91-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="2ea91-235">L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="2ea91-236">Exécutez l’outil dans une invite de commandes d’administrateur sur Windows et avec `sudo` sur MacOS.</span><span class="sxs-lookup"><span data-stu-id="2ea91-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="2ea91-237">Les `dry-run` `whatif` commandes et ne nécessitent pas d’élévation.</span><span class="sxs-lookup"><span data-stu-id="2ea91-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="2ea91-238">**dotnet-Core-désinstaller supprimer**</span><span class="sxs-lookup"><span data-stu-id="2ea91-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="2ea91-239">Synopsis</span><span class="sxs-lookup"><span data-stu-id="2ea91-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="2ea91-240">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ea91-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="2ea91-241">Version spécifiée à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ea91-241">The specified version to uninstall.</span></span> <span data-ttu-id="2ea91-242">Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="2ea91-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="2ea91-243">Les fichiers réponse sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2ea91-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="2ea91-244">Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2ea91-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="2ea91-245">Il s’agit de fichiers texte, généralement avec une \* extension. rsp, et chaque version est indiquée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="2ea91-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="2ea91-246">Pour spécifier un fichier réponse pour l' `VERSION` argument, utilisez le \@ caractère immédiatement suivi du nom du fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="2ea91-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="2ea91-247">Options</span><span class="sxs-lookup"><span data-stu-id="2ea91-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="2ea91-248">Windows</span><span class="sxs-lookup"><span data-stu-id="2ea91-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="2ea91-249">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-250">Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="2ea91-251">La version spécifiée reste installée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-252">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2ea91-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="2ea91-253">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2ea91-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="2ea91-254">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="2ea91-255">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="2ea91-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="2ea91-256">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="2ea91-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="2ea91-257">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="2ea91-258">Supprime ASP.NET Core runtimes uniquement.</span><span class="sxs-lookup"><span data-stu-id="2ea91-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="2ea91-259">Supprime uniquement les regroupements d’hébergement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="2ea91-260">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="2ea91-261">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-262">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-263">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-263">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-264">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-265">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="2ea91-266">Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.</span><span class="sxs-lookup"><span data-stu-id="2ea91-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="2ea91-267">Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.</span><span class="sxs-lookup"><span data-stu-id="2ea91-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="2ea91-268">**`-y, --yes`** Exécute la commande sans demander de confirmation oui ou non.</span><span class="sxs-lookup"><span data-stu-id="2ea91-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="2ea91-269">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ea91-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="2ea91-270">Remarques :</span><span class="sxs-lookup"><span data-stu-id="2ea91-270">Notes:</span></span>

1. <span data-ttu-id="2ea91-271">Exactement l’un des `--sdk` ,, `--runtime` `--aspnet-runtime` et `--hosting-bundle` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2ea91-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="2ea91-272">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="2ea91-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="2ea91-273">Si `--x64` ou `--x86` n’est pas spécifié, les paramètres x64 et x86 seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="2ea91-274">macOS</span><span class="sxs-lookup"><span data-stu-id="2ea91-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="2ea91-275">Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="2ea91-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-276">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="2ea91-277">La version spécifiée est conservée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="2ea91-278">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2ea91-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="2ea91-279">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2ea91-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="2ea91-280">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="2ea91-281">Cette option protège global. JSON.</span><span class="sxs-lookup"><span data-stu-id="2ea91-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="2ea91-282">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.</span><span class="sxs-lookup"><span data-stu-id="2ea91-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="2ea91-283">Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="2ea91-284">Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea91-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="2ea91-285">Supprime uniquement les runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="2ea91-286">Supprime uniquement les kits de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ea91-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="2ea91-287">Définit le niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="2ea91-287">Sets the verbosity level.</span></span> <span data-ttu-id="2ea91-288">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2ea91-289">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-289">The default value is `normal`.</span></span>

* <span data-ttu-id="2ea91-290">**`-y, --yes`** Exécute la commande sans demander de confirmation Y/N.</span><span class="sxs-lookup"><span data-stu-id="2ea91-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="2ea91-291">**`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="2ea91-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="2ea91-292">Remarques :</span><span class="sxs-lookup"><span data-stu-id="2ea91-292">Notes:</span></span>

1. <span data-ttu-id="2ea91-293">Une seule `--sdk` et unique `--runtime` est requise.</span><span class="sxs-lookup"><span data-stu-id="2ea91-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="2ea91-294">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="2ea91-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="2ea91-295">Exemples</span><span class="sxs-lookup"><span data-stu-id="2ea91-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="2ea91-296">Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK) sont conservés.</span><span class="sxs-lookup"><span data-stu-id="2ea91-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="2ea91-297">Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent être conservés, en fonction de l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ea91-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="2ea91-298">Pour supprimer tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l' `--force` option.</span><span class="sxs-lookup"><span data-stu-id="2ea91-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="2ea91-299">Supprimez tous les runtimes .NET Core à l’exception de la version `3.0.0-preview6-27804-01` sans demander de confirmation Y/N :</span><span class="sxs-lookup"><span data-stu-id="2ea91-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="2ea91-300">Supprimer tous les kits de développement logiciel (SDK) .NET Core 1,1 sans demander de confirmation Y/n :</span><span class="sxs-lookup"><span data-stu-id="2ea91-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="2ea91-301">Supprimez le kit de développement logiciel (SDK) .NET Core 1.1.11 au minimum sans sortie de la console :</span><span class="sxs-lookup"><span data-stu-id="2ea91-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="2ea91-302">Supprimez tous les kits de développement logiciel (SDK) .NET Core pouvant être supprimés en toute sécurité par cet outil :</span><span class="sxs-lookup"><span data-stu-id="2ea91-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="2ea91-303">Supprimer tous les kits de développement logiciel (SDK) .NET Core qui peuvent être supprimés par cet outil, y compris les kits de développement logiciel (SDK) qui peuvent être requis par Visual Studio (non recommandé) :</span><span class="sxs-lookup"><span data-stu-id="2ea91-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="2ea91-304">Supprimer tous les kits de développement logiciel (SDK) .NET Core spécifiés dans le fichier réponse`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="2ea91-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="2ea91-305">Le contenu de *versions. rsp* est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2ea91-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="2ea91-306">Étape 4 : supprimer le dossier NuGet Fallback (facultatif)</span><span class="sxs-lookup"><span data-stu-id="2ea91-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="2ea91-307">Dans certains cas, vous n’avez plus besoin de la et vous souhaiterez `NuGetFallbackFolder` peut-être la supprimer.</span><span class="sxs-lookup"><span data-stu-id="2ea91-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="2ea91-308">Pour plus d’informations sur la suppression de ce dossier, consultez [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="2ea91-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="2ea91-309">Désinstaller l’outil</span><span class="sxs-lookup"><span data-stu-id="2ea91-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="2ea91-310">Windows</span><span class="sxs-lookup"><span data-stu-id="2ea91-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="2ea91-311">Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="2ea91-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="2ea91-312">Recherchez `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="2ea91-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="2ea91-313">Sélectionner **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="2ea91-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="2ea91-314">macOS</span><span class="sxs-lookup"><span data-stu-id="2ea91-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="2ea91-315">Supprimez le fichier *dotnet-Core-Uninstall. tar. gz* téléchargé à partir du répertoire où il a été installé.</span><span class="sxs-lookup"><span data-stu-id="2ea91-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="2ea91-316">Si vous dézippéz le contenu de ce fichier dans un autre répertoire, veillez à supprimer également ce contenu.</span><span class="sxs-lookup"><span data-stu-id="2ea91-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
