---
title: Commande dotnet tool uninstall
description: La commande de désinstallation de l’outil dotnet désinstalle l’outil .NET spécifié de votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634088"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="b4835-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="b4835-103">dotnet tool uninstall</span></span>

<span data-ttu-id="b4835-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b4835-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b4835-105">Name</span><span class="sxs-lookup"><span data-stu-id="b4835-105">Name</span></span>

<span data-ttu-id="b4835-106">`dotnet tool uninstall` -Désinstalle l' [outil .net](global-tools.md) spécifié de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b4835-106">`dotnet tool uninstall` - Uninstalls the specified [.NET tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b4835-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b4835-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="b4835-108">Description</span><span class="sxs-lookup"><span data-stu-id="b4835-108">Description</span></span>

<span data-ttu-id="b4835-109">La `dotnet tool uninstall` commande vous permet de désinstaller les outils .net de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b4835-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET tools from your machine.</span></span> <span data-ttu-id="b4835-110">Pour utiliser la commande, vous spécifiez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4835-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="b4835-111">Pour désinstaller un outil global qui a été installé à l’emplacement par défaut, utilisez l' `--global` option.</span><span class="sxs-lookup"><span data-stu-id="b4835-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="b4835-112">Pour désinstaller un outil global qui a été installé dans un emplacement personnalisé, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="b4835-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="b4835-113">Pour désinstaller un outil local, omettez `--global` les `--tool-path` options et.</span><span class="sxs-lookup"><span data-stu-id="b4835-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="b4835-114">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="b4835-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="b4835-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4835-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="b4835-116">Nom/ID du package NuGet qui contient l’outil .NET à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="b4835-116">Name/ID of the NuGet package that contains the .NET tool to uninstall.</span></span> <span data-ttu-id="b4835-117">Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="b4835-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="b4835-118">Options</span><span class="sxs-lookup"><span data-stu-id="b4835-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="b4835-119">Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4835-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="b4835-120">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="b4835-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b4835-121">En omettant les deux `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="b4835-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b4835-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="b4835-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="b4835-123">Spécifie l’emplacement de désinstallation de l’outil.</span><span class="sxs-lookup"><span data-stu-id="b4835-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="b4835-124">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="b4835-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="b4835-125">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="b4835-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="b4835-126">En omettant les deux `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="b4835-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="b4835-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="b4835-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="b4835-128">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="b4835-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="b4835-129">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="b4835-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="b4835-130">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Linux/MacOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="b4835-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="b4835-131">Désinstalle l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="b4835-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4835-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4835-132">See also</span></span>

- [<span data-ttu-id="b4835-133">Outils .NET</span><span class="sxs-lookup"><span data-stu-id="b4835-133">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="b4835-134">Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="b4835-134">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="b4835-135">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="b4835-135">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
