---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre machine.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463345"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="f6399-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="f6399-103">dotnet tool list</span></span>

<span data-ttu-id="f6399-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f6399-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6399-105">Nom</span><span class="sxs-lookup"><span data-stu-id="f6399-105">Name</span></span>

<span data-ttu-id="f6399-106">`dotnet tool list`- Répertorie tous les [outils .NET Core](global-tools.md) du type spécifié actuellement installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="f6399-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6399-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f6399-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="f6399-108">Description</span><span class="sxs-lookup"><span data-stu-id="f6399-108">Description</span></span>

<span data-ttu-id="f6399-109">La `dotnet tool list` commande vous permet d’énumérer tous les outils globaux.NET Core, tool-path ou locaux installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="f6399-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="f6399-110">La commande répertorie le nom du paquet, la version installée et la commande de l’outil.</span><span class="sxs-lookup"><span data-stu-id="f6399-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="f6399-111">Pour utiliser la commande, vous spécifiez l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f6399-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="f6399-112">Un outil global installé dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6399-112">A global tool installed in the default location.</span></span> <span data-ttu-id="f6399-113">Utiliser `--global` l’option</span><span class="sxs-lookup"><span data-stu-id="f6399-113">Use the `--global` option</span></span>
* <span data-ttu-id="f6399-114">Un outil global installé dans un emplacement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6399-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="f6399-115">Utilisez l'option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="f6399-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="f6399-116">Un outil local.</span><span class="sxs-lookup"><span data-stu-id="f6399-116">A local tool.</span></span> <span data-ttu-id="f6399-117">Omettre `--global` `--tool-path` les options et les options.</span><span class="sxs-lookup"><span data-stu-id="f6399-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f6399-118">**Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="f6399-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="f6399-119">Options</span><span class="sxs-lookup"><span data-stu-id="f6399-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="f6399-120">Répertorie les outils mondiaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f6399-120">Lists user-wide global tools.</span></span> <span data-ttu-id="f6399-121">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="f6399-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f6399-122">L’omission `--global` des `--tool-path` deux et la liste des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="f6399-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f6399-123">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f6399-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f6399-124">Spécifie un emplacement personnalisé où trouver des outils globaux.</span><span class="sxs-lookup"><span data-stu-id="f6399-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="f6399-125">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="f6399-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="f6399-126">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="f6399-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f6399-127">L’omission `--global` des `--tool-path` deux et la liste des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="f6399-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="f6399-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="f6399-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="f6399-129">Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel).</span><span class="sxs-lookup"><span data-stu-id="f6399-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="f6399-130">Répertorie les outils globaux à partir d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="f6399-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="f6399-131">Répertorie les outils globaux à partir d’un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="f6399-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="f6399-132">Répertorie tous les outils locaux disponibles dans l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="f6399-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6399-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6399-133">See also</span></span>

- [<span data-ttu-id="f6399-134">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="f6399-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f6399-135">Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="f6399-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f6399-136">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="f6399-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
