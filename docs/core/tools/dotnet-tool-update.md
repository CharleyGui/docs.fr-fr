---
title: Commande dotnet tool update
description: La commande de mise à jour de l’outil dotnet met à jour l’outil .NET Core spécifié sur votre ordinateur.
ms.date: 07/08/2020
ms.openlocfilehash: a212fbb40af68019c1bc9a63963d960292be6b08
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308869"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="9853f-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="9853f-103">dotnet tool update</span></span>

<span data-ttu-id="9853f-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9853f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9853f-105">Nom</span><span class="sxs-lookup"><span data-stu-id="9853f-105">Name</span></span>

<span data-ttu-id="9853f-106">`dotnet tool update`-Met à jour l' [outil .net Core](global-tools.md) spécifié sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9853f-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9853f-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9853f-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="9853f-108">Description</span><span class="sxs-lookup"><span data-stu-id="9853f-108">Description</span></span>

<span data-ttu-id="9853f-109">La `dotnet tool update` commande vous permet de mettre à jour les outils .net Core sur votre ordinateur vers la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="9853f-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="9853f-110">La commande désinstalle et réinstalle un outil en le mettant à jour.</span><span class="sxs-lookup"><span data-stu-id="9853f-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="9853f-111">Pour utiliser la commande, vous spécifiez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="9853f-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="9853f-112">Pour mettre à jour un outil global qui a été installé à l’emplacement par défaut, utilisez l' `--global` option</span><span class="sxs-lookup"><span data-stu-id="9853f-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="9853f-113">Pour mettre à jour un outil global qui a été installé dans un emplacement personnalisé, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="9853f-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="9853f-114">Pour mettre à jour un outil local, utilisez l' `--local` option.</span><span class="sxs-lookup"><span data-stu-id="9853f-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="9853f-115">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="9853f-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="9853f-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="9853f-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="9853f-117">Nom/ID du package NuGet qui contient l’outil Global .NET Core à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="9853f-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="9853f-118">Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="9853f-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="9853f-119">Options</span><span class="sxs-lookup"><span data-stu-id="9853f-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="9853f-120">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="9853f-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="9853f-121">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9853f-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="9853f-122">Empêcher la restauration en parallèle de plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="9853f-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="9853f-123">Spécifie le [framework cible](../../standard/frameworks.md) pour lequel mettre à jour l’outil.</span><span class="sxs-lookup"><span data-stu-id="9853f-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="9853f-124">Considérer les défaillances de la source du package comme des avertissements.</span><span class="sxs-lookup"><span data-stu-id="9853f-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="9853f-125">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="9853f-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="9853f-126">Mettez à jour l’outil et le manifeste de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="9853f-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="9853f-127">Ne peut pas être combiné avec l' `--global` option ou l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="9853f-127">Can't be combined with the `--global` option or the `--tool-path` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="9853f-128">Ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="9853f-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="9853f-129">Chemin d’accès au fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="9853f-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="9853f-130">Spécifie l’emplacement d’installation de l’outil Global.</span><span class="sxs-lookup"><span data-stu-id="9853f-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="9853f-131">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="9853f-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="9853f-132">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="9853f-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="9853f-133">En omettant les deux `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.</span><span class="sxs-lookup"><span data-stu-id="9853f-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="9853f-134">Plage de versions du package d’outils à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="9853f-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="9853f-135">Cela ne peut pas être utilisé pour rétrograder des versions, vous devez d’abord disposer d’une `uninstall` version plus récente.</span><span class="sxs-lookup"><span data-stu-id="9853f-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="9853f-136">Spécifie que la mise à jour concerne un outil à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9853f-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="9853f-137">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="9853f-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="9853f-138">En omettant les deux `--global` et `--tool-path` spécifie que l’outil à mettre à jour est un outil local.</span><span class="sxs-lookup"><span data-stu-id="9853f-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9853f-139">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="9853f-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9853f-140">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="9853f-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9853f-141">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9853f-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="9853f-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="9853f-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="9853f-143">Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="9853f-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="9853f-144">Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="9853f-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="9853f-145">Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Linux/MacOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="9853f-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="9853f-146">Met à jour l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) installé pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="9853f-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="9853f-147">Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) avec la dernière version du correctif, avec une version principale de `2` et une version mineure de `0` .</span><span class="sxs-lookup"><span data-stu-id="9853f-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="9853f-148">Met à jour l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) avec la version la plus basse dans la plage spécifiée `(> 2.0.0 && < 2.1.4)` , la version est `2.1.0` installée.</span><span class="sxs-lookup"><span data-stu-id="9853f-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="9853f-149">Pour plus d’informations sur les plages de contrôle de version sémantique, consultez [plages de versions d’empaquetage NuGet](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="9853f-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="9853f-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9853f-150">See also</span></span>

- [<span data-ttu-id="9853f-151">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="9853f-151">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="9853f-152">Gestion sémantique de version</span><span class="sxs-lookup"><span data-stu-id="9853f-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="9853f-153">Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="9853f-153">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="9853f-154">Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="9853f-154">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
