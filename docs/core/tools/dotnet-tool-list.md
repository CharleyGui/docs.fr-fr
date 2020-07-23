---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925460"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="c6425-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c6425-103">dotnet tool list</span></span>

<span data-ttu-id="c6425-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="c6425-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c6425-105">Nom</span><span class="sxs-lookup"><span data-stu-id="c6425-105">Name</span></span>

<span data-ttu-id="c6425-106">`dotnet tool list`-Répertorie tous les [outils .net Core](global-tools.md) du type spécifié actuellement installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c6425-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6425-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c6425-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="c6425-108">Description</span><span class="sxs-lookup"><span data-stu-id="c6425-108">Description</span></span>

<span data-ttu-id="c6425-109">La `dotnet tool list` commande vous permet de répertorier tous les outils globaux, de chemin d’accès d’outil ou d’outils locaux .net Core installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c6425-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="c6425-110">La commande répertorie le nom du package, la version installée et la commande d’outil.</span><span class="sxs-lookup"><span data-stu-id="c6425-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="c6425-111">Pour utiliser la commande, vous spécifiez l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c6425-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="c6425-112">Pour répertorier les outils globaux installés à l’emplacement par défaut, utilisez l' `--global` option</span><span class="sxs-lookup"><span data-stu-id="c6425-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="c6425-113">Pour répertorier les outils globaux installés dans un emplacement personnalisé, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="c6425-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="c6425-114">Pour répertorier les outils locaux, utilisez l' `--local` option ou omettez les `--global` `--tool-path` options, et `--local` .</span><span class="sxs-lookup"><span data-stu-id="c6425-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="c6425-115">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="c6425-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="c6425-116">Options</span><span class="sxs-lookup"><span data-stu-id="c6425-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="c6425-117">Répertorie les outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c6425-117">Lists user-wide global tools.</span></span> <span data-ttu-id="c6425-118">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="c6425-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c6425-119">L’omission `--global` de et `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="c6425-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c6425-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="c6425-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="c6425-121">Répertorie les outils locaux pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c6425-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="c6425-122">Ne peut pas être combiné avec les `--global` `--tool-path` options ou.</span><span class="sxs-lookup"><span data-stu-id="c6425-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="c6425-123">L’omission `--global` de et `--tool-path` répertorie les outils locaux même si `--local` n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="c6425-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="c6425-124">Spécifie un emplacement personnalisé où trouver les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="c6425-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="c6425-125">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="c6425-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="c6425-126">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="c6425-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c6425-127">L’omission `--global` de et `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="c6425-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="c6425-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="c6425-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="c6425-129">Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre ordinateur (profil utilisateur actuel).</span><span class="sxs-lookup"><span data-stu-id="c6425-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="c6425-130">Répertorie les outils globaux d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="c6425-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="c6425-131">Répertorie les outils globaux d’un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="c6425-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="c6425-132">**`dotnet tool list`** ni**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="c6425-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="c6425-133">Répertorie tous les outils locaux disponibles dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c6425-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6425-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6425-134">See also</span></span>

- [<span data-ttu-id="c6425-135">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6425-135">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="c6425-136">Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6425-136">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c6425-137">Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6425-137">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
