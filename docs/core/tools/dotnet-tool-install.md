---
title: Commande dotnet tool install
description: La commande d’installation de l’outil dotnet installe l’outil .NET Core spécifié sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 837d12bc807ad95ccdbd9c0e087c7d45418c6e74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626032"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="fadf3-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="fadf3-103">dotnet tool install</span></span>

<span data-ttu-id="fadf3-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="fadf3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fadf3-105">Name</span><span class="sxs-lookup"><span data-stu-id="fadf3-105">Name</span></span>

<span data-ttu-id="fadf3-106">`dotnet tool install` : installe l' [outil .net Core](global-tools.md) spécifié sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fadf3-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fadf3-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="fadf3-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="fadf3-108">Description</span><span class="sxs-lookup"><span data-stu-id="fadf3-108">Description</span></span>

<span data-ttu-id="fadf3-109">La commande `dotnet tool install` vous permet d’installer les outils .NET Core sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fadf3-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="fadf3-110">Pour utiliser la commande, vous spécifiez l’une des options d’installation suivantes :</span><span class="sxs-lookup"><span data-stu-id="fadf3-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="fadf3-111">Pour installer un outil Global à l’emplacement par défaut, utilisez l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="fadf3-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="fadf3-112">Pour installer un outil Global dans un emplacement personnalisé, utilisez l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="fadf3-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="fadf3-113">Pour installer un outil local, omettez les options `--global` et `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="fadf3-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="fadf3-114">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="fadf3-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="fadf3-115">Les outils globaux sont installés par défaut dans les répertoires suivants lorsque vous spécifiez l’option `-g` ou `--global` :</span><span class="sxs-lookup"><span data-stu-id="fadf3-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="fadf3-116">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="fadf3-116">OS</span></span>          | <span data-ttu-id="fadf3-117">Path</span><span class="sxs-lookup"><span data-stu-id="fadf3-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="fadf3-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="fadf3-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="fadf3-119">Windows</span><span class="sxs-lookup"><span data-stu-id="fadf3-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="fadf3-120">Les outils locaux sont ajoutés à un fichier *Tool-manifest. JSON* dans un répertoire *. config* sous le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fadf3-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="fadf3-121">Si un fichier manifeste n’existe pas encore, créez-le en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fadf3-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="fadf3-122">Pour plus d’informations, consultez [installer un outil local](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="fadf3-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="fadf3-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="fadf3-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="fadf3-124">Nom/ID du package NuGet qui contient l’outil .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="fadf3-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="fadf3-125">Options</span><span class="sxs-lookup"><span data-stu-id="fadf3-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="fadf3-126">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="fadf3-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="fadf3-127">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fadf3-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="fadf3-128">Spécifie le [framework cible](../../standard/frameworks.md) pour lequel installer l’outil.</span><span class="sxs-lookup"><span data-stu-id="fadf3-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="fadf3-129">Par défaut, le SDK .NET Core essaie de choisir le framework cible le plus approprié.</span><span class="sxs-lookup"><span data-stu-id="fadf3-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="fadf3-130">Spécifie que l’installation est à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fadf3-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="fadf3-131">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="fadf3-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="fadf3-132">L’omission des `--global` et `--tool-path` spécifie une installation de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="fadf3-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="fadf3-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="fadf3-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="fadf3-134">Spécifie l’emplacement d’installation de l’outil global.</span><span class="sxs-lookup"><span data-stu-id="fadf3-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="fadf3-135">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="fadf3-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="fadf3-136">Si le chemin n’existe pas, la commande essaie de le créer.</span><span class="sxs-lookup"><span data-stu-id="fadf3-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="fadf3-137">L’omission des `--global` et `--tool-path` spécifie une installation de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="fadf3-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fadf3-138">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="fadf3-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fadf3-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="fadf3-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="fadf3-140">Version de l’outil à installer.</span><span class="sxs-lookup"><span data-stu-id="fadf3-140">The version of the tool to install.</span></span> <span data-ttu-id="fadf3-141">Par défaut, la dernière version stable du package est installée.</span><span class="sxs-lookup"><span data-stu-id="fadf3-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="fadf3-142">Utilisez cette option pour installer la préversion ou des versions antérieures de l’outil.</span><span class="sxs-lookup"><span data-stu-id="fadf3-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="fadf3-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="fadf3-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="fadf3-144">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="fadf3-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="fadf3-145">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="fadf3-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="fadf3-146">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) comme un outil Global dans un répertoire Linux/MacOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="fadf3-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="fadf3-147">Installe la version 2.0.0 de [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil Global.</span><span class="sxs-lookup"><span data-stu-id="fadf3-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="fadf3-148">Installe [dotnetsay](https://www.nuget.org/packages/dotnetsay/) en tant qu’outil local pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fadf3-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fadf3-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fadf3-149">See also</span></span>

- [<span data-ttu-id="fadf3-150">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="fadf3-150">.NET Core tools</span></span>](global-tools.md)
