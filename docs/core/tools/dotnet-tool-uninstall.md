---
title: Commande dotnet tool uninstall
description: L’outil dotnet désinstalle la commande désinstalle l’outil spécifié .NET Core de votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463312"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="f51aa-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="f51aa-103">dotnet tool uninstall</span></span>

<span data-ttu-id="f51aa-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f51aa-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f51aa-105">Nom</span><span class="sxs-lookup"><span data-stu-id="f51aa-105">Name</span></span>

<span data-ttu-id="f51aa-106">`dotnet tool uninstall`- Désinstalle [l’outil spécifié .NET Core](global-tools.md) de votre machine.</span><span class="sxs-lookup"><span data-stu-id="f51aa-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f51aa-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f51aa-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="f51aa-108">Description</span><span class="sxs-lookup"><span data-stu-id="f51aa-108">Description</span></span>

<span data-ttu-id="f51aa-109">La `dotnet tool uninstall` commande vous permet de désinstaller les outils .NET Core de votre machine.</span><span class="sxs-lookup"><span data-stu-id="f51aa-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="f51aa-110">Pour utiliser la commande, vous spécifiez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="f51aa-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="f51aa-111">Pour désinstaller un outil global qui a été `--global` installé dans l’emplacement par défaut, utilisez l’option.</span><span class="sxs-lookup"><span data-stu-id="f51aa-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="f51aa-112">Pour désinstaller un outil global qui a été `--tool-path` installé dans un emplacement personnalisé, utilisez l’option.</span><span class="sxs-lookup"><span data-stu-id="f51aa-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="f51aa-113">Pour désinstaller un outil local, `--tool-path` omettre les options et les `--global` options.</span><span class="sxs-lookup"><span data-stu-id="f51aa-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f51aa-114">**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="f51aa-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="f51aa-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="f51aa-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f51aa-116">Nom/ID du paquet NuGet qui contient l’outil .NET Core pour désinstaller.</span><span class="sxs-lookup"><span data-stu-id="f51aa-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="f51aa-117">Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="f51aa-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f51aa-118">Options</span><span class="sxs-lookup"><span data-stu-id="f51aa-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="f51aa-119">Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f51aa-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="f51aa-120">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="f51aa-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f51aa-121">L’omission `--global` à `--tool-path` la fois et précise que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="f51aa-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f51aa-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f51aa-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f51aa-123">Spécifie l’emplacement où désinstaller l’outil.</span><span class="sxs-lookup"><span data-stu-id="f51aa-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="f51aa-124">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="f51aa-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="f51aa-125">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="f51aa-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f51aa-126">L’omission `--global` à `--tool-path` la fois et précise que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="f51aa-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="f51aa-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="f51aa-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="f51aa-128">Désinstalle l’outil mondial [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="f51aa-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f51aa-129">Désinstalle l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="f51aa-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f51aa-130">Désinstalle l’outil mondial [dotnetsay](https://www.nuget.org/packages/dotnetsay/) à partir d’un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="f51aa-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="f51aa-131">Désinstalle l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="f51aa-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f51aa-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51aa-132">See also</span></span>

- [<span data-ttu-id="f51aa-133">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="f51aa-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f51aa-134">Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="f51aa-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f51aa-135">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="f51aa-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
