---
title: Commande dotnet tool uninstall
description: La commande de désinstallation de l’outil dotnet désinstalle l’outil .NET Core spécifié de votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157043"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="69174-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="69174-103">dotnet tool uninstall</span></span>

<span data-ttu-id="69174-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="69174-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="69174-105">Nom</span><span class="sxs-lookup"><span data-stu-id="69174-105">Name</span></span>

<span data-ttu-id="69174-106">`dotnet tool uninstall`-désinstalle l' [outil .net Core](global-tools.md) spécifié de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="69174-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="69174-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="69174-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="69174-108">Description</span><span class="sxs-lookup"><span data-stu-id="69174-108">Description</span></span>

<span data-ttu-id="69174-109">La commande `dotnet tool uninstall` vous permet de désinstaller les outils .NET Core de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="69174-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="69174-110">Pour utiliser la commande, vous spécifiez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="69174-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="69174-111">Pour désinstaller un outil global qui a été installé à l’emplacement par défaut, utilisez l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="69174-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="69174-112">Pour désinstaller un outil global qui a été installé dans un emplacement personnalisé, utilisez l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="69174-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="69174-113">Pour désinstaller un outil local, omettez les options `--global` et `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="69174-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="69174-114">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="69174-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="69174-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="69174-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="69174-116">Nom/ID du package NuGet qui contient l’outil .NET Core à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="69174-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="69174-117">Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="69174-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="69174-118">Options</span><span class="sxs-lookup"><span data-stu-id="69174-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="69174-119">Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="69174-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="69174-120">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="69174-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="69174-121">L’omission de `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="69174-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="69174-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="69174-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="69174-123">Spécifie l’emplacement de désinstallation de l’outil.</span><span class="sxs-lookup"><span data-stu-id="69174-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="69174-124">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="69174-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="69174-125">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="69174-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="69174-126">L’omission de `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.</span><span class="sxs-lookup"><span data-stu-id="69174-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="69174-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="69174-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="69174-128">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="69174-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="69174-129">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="69174-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="69174-130">Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Linux/MacOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="69174-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="69174-131">Désinstalle l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="69174-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="69174-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69174-132">See also</span></span>

- [<span data-ttu-id="69174-133">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="69174-133">.NET Core tools</span></span>](global-tools.md)
