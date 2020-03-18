---
title: Commande dotnet tool update
description: La commande de mise à jour d’outil pointnet met à jour l’outil net Core spécifié sur votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847818"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="af2f0-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="af2f0-103">dotnet tool update</span></span>

<span data-ttu-id="af2f0-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="af2f0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="af2f0-105">Nom</span><span class="sxs-lookup"><span data-stu-id="af2f0-105">Name</span></span>

<span data-ttu-id="af2f0-106">`dotnet tool update`- Mise à jour de [l’outil net Core](global-tools.md) spécifié sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="af2f0-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="af2f0-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="af2f0-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="af2f0-108">Description</span><span class="sxs-lookup"><span data-stu-id="af2f0-108">Description</span></span>

<span data-ttu-id="af2f0-109">La `dotnet tool update` commande vous permet de mettre à jour les outils .NET Core de votre machine à la dernière version stable du paquet.</span><span class="sxs-lookup"><span data-stu-id="af2f0-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="af2f0-110">La commande désinstalle et réinstalle un outil en le mettant à jour.</span><span class="sxs-lookup"><span data-stu-id="af2f0-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="af2f0-111">Pour utiliser la commande, vous spécifiez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="af2f0-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="af2f0-112">Pour mettre à jour un outil global qui `--global` a été installé dans l’emplacement par défaut, utilisez l’option</span><span class="sxs-lookup"><span data-stu-id="af2f0-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="af2f0-113">Pour mettre à jour un outil global qui `--tool-path` a été installé dans un emplacement personnalisé, utilisez l’option.</span><span class="sxs-lookup"><span data-stu-id="af2f0-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="af2f0-114">Pour mettre à jour un `--global` `--tool-path` outil local, omettre les options et les options.</span><span class="sxs-lookup"><span data-stu-id="af2f0-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="af2f0-115">**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="af2f0-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="af2f0-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="af2f0-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="af2f0-117">Nom/ID du paquet NuGet qui contient l’outil mondial .NET Core à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="af2f0-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="af2f0-118">Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="af2f0-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="af2f0-119">Options</span><span class="sxs-lookup"><span data-stu-id="af2f0-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="af2f0-120">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="af2f0-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="af2f0-121">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="af2f0-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="af2f0-122">Spécifie le [framework cible](../../standard/frameworks.md) pour lequel mettre à jour l’outil.</span><span class="sxs-lookup"><span data-stu-id="af2f0-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="af2f0-123">Spécifie que la mise à jour concerne un outil à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af2f0-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="af2f0-124">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="af2f0-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="af2f0-125">L’omission `--global` à `--tool-path` la fois et précise que l’outil à mettre à jour est un outil local.</span><span class="sxs-lookup"><span data-stu-id="af2f0-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="af2f0-126">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="af2f0-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="af2f0-127">Précise l’emplacement où l’outil global est installé.</span><span class="sxs-lookup"><span data-stu-id="af2f0-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="af2f0-128">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="af2f0-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="af2f0-129">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="af2f0-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="af2f0-130">L’omission `--global` à `--tool-path` la fois et précise que l’outil à mettre à jour est un outil local.</span><span class="sxs-lookup"><span data-stu-id="af2f0-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="af2f0-131">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="af2f0-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="af2f0-132">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="af2f0-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="af2f0-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="af2f0-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="af2f0-134">Mise à jour de l’outil mondial [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="af2f0-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="af2f0-135">Mise à jour de [l’outil global dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="af2f0-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="af2f0-136">Mise à jour de [l’outil mondial dotnetsay](https://www.nuget.org/packages/dotnetsay/) situé dans un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="af2f0-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="af2f0-137">Mise à jour de [l’outil local dotnetsay](https://www.nuget.org/packages/dotnetsay/) installé pour l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="af2f0-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="af2f0-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af2f0-138">See also</span></span>

- [<span data-ttu-id="af2f0-139">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="af2f0-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="af2f0-140">Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="af2f0-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="af2f0-141">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="af2f0-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
