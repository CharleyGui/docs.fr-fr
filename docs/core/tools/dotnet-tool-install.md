---
title: Commande dotnet tool install
description: La commande d’installation de l’outil dotnet installe l’outil .NET Core spécifié sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702814"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="1fd61-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="1fd61-103">dotnet tool install</span></span>

<span data-ttu-id="1fd61-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1fd61-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1fd61-105">Nom</span><span class="sxs-lookup"><span data-stu-id="1fd61-105">Name</span></span>

<span data-ttu-id="1fd61-106">`dotnet tool install`-Installe l' [outil .net Core](global-tools.md) spécifié sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1fd61-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1fd61-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="1fd61-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="1fd61-108">Description</span><span class="sxs-lookup"><span data-stu-id="1fd61-108">Description</span></span>

<span data-ttu-id="1fd61-109">La `dotnet tool install` commande vous permet d’installer les outils .net Core sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1fd61-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="1fd61-110">Pour utiliser la commande, vous spécifiez l’une des options d’installation suivantes :</span><span class="sxs-lookup"><span data-stu-id="1fd61-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="1fd61-111">Pour installer un outil Global dans l’emplacement par défaut, utilisez l' `--global` option.</span><span class="sxs-lookup"><span data-stu-id="1fd61-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="1fd61-112">Pour installer un outil Global dans un emplacement personnalisé, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="1fd61-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="1fd61-113">Pour installer un outil local, omettez les `--global` `--tool-path` options et.</span><span class="sxs-lookup"><span data-stu-id="1fd61-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="1fd61-114">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="1fd61-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="1fd61-115">Les outils globaux sont installés par défaut dans les répertoires suivants lorsque vous spécifiez l' `-g` `--global` option ou :</span><span class="sxs-lookup"><span data-stu-id="1fd61-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="1fd61-116">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="1fd61-116">OS</span></span>          | <span data-ttu-id="1fd61-117">Path</span><span class="sxs-lookup"><span data-stu-id="1fd61-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="1fd61-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="1fd61-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="1fd61-119">Windows</span><span class="sxs-lookup"><span data-stu-id="1fd61-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="1fd61-120">Les outils locaux sont ajoutés à un fichier *dotnet-Tools. JSON* dans un répertoire *. config* sous le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="1fd61-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="1fd61-121">Si un fichier manifeste n’existe pas encore, créez-le en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1fd61-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="1fd61-122">Pour plus d’informations, consultez [installer un outil local](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="1fd61-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="1fd61-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="1fd61-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="1fd61-124">Nom/ID du package NuGet qui contient l’outil .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="1fd61-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="1fd61-125">Options</span><span class="sxs-lookup"><span data-stu-id="1fd61-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="1fd61-126">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="1fd61-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="1fd61-127">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1fd61-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="1fd61-128">Spécifie le [framework cible](../../standard/frameworks.md) pour lequel installer l’outil.</span><span class="sxs-lookup"><span data-stu-id="1fd61-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="1fd61-129">Par défaut, le SDK .NET Core essaie de choisir le framework cible le plus approprié.</span><span class="sxs-lookup"><span data-stu-id="1fd61-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="1fd61-130">Spécifie que l’installation est à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1fd61-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="1fd61-131">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="1fd61-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="1fd61-132">En omettant les deux `--global` et `--tool-path` spécifie une installation de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="1fd61-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1fd61-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1fd61-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="1fd61-134">Spécifie l’emplacement d’installation de l’outil global.</span><span class="sxs-lookup"><span data-stu-id="1fd61-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="1fd61-135">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="1fd61-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="1fd61-136">Si le chemin n’existe pas, la commande essaie de le créer.</span><span class="sxs-lookup"><span data-stu-id="1fd61-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="1fd61-137">En omettant les deux `--global` et `--tool-path` spécifie une installation de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="1fd61-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1fd61-138">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="1fd61-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1fd61-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1fd61-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="1fd61-140">Version de l’outil à installer.</span><span class="sxs-lookup"><span data-stu-id="1fd61-140">The version of the tool to install.</span></span> <span data-ttu-id="1fd61-141">Par défaut, la dernière version stable du package est installée.</span><span class="sxs-lookup"><span data-stu-id="1fd61-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="1fd61-142">Utilisez cette option pour installer la préversion ou des versions antérieures de l’outil.</span><span class="sxs-lookup"><span data-stu-id="1fd61-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="1fd61-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="1fd61-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="1fd61-144">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="1fd61-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="1fd61-145">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="1fd61-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="1fd61-146">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Linux/MacOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="1fd61-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="1fd61-147">Installe la version 2.0.0 de [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil Global.</span><span class="sxs-lookup"><span data-stu-id="1fd61-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="1fd61-148">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil local pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="1fd61-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fd61-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fd61-149">See also</span></span>

- [<span data-ttu-id="1fd61-150">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="1fd61-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="1fd61-151">Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="1fd61-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="1fd61-152">Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="1fd61-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
