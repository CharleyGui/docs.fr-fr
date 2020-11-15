---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET installés sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634283"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="29642-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="29642-103">dotnet tool list</span></span>

<span data-ttu-id="29642-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="29642-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="29642-105">Name</span><span class="sxs-lookup"><span data-stu-id="29642-105">Name</span></span>

<span data-ttu-id="29642-106">`dotnet tool list` -Répertorie tous les [outils .net](global-tools.md) du type spécifié actuellement installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29642-106">`dotnet tool list` - Lists all [.NET tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="29642-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="29642-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="29642-108">Description</span><span class="sxs-lookup"><span data-stu-id="29642-108">Description</span></span>

<span data-ttu-id="29642-109">La `dotnet tool list` commande vous permet de répertorier tous les outils .NET globaux, de chemin d’accès d’outils ou locaux installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29642-109">The `dotnet tool list` command provides a way for you to list all .NET global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="29642-110">La commande répertorie le nom du package, la version installée et la commande d’outil.</span><span class="sxs-lookup"><span data-stu-id="29642-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="29642-111">Pour utiliser la commande, vous spécifiez l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="29642-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="29642-112">Pour répertorier les outils globaux installés à l’emplacement par défaut, utilisez l' `--global` option</span><span class="sxs-lookup"><span data-stu-id="29642-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="29642-113">Pour répertorier les outils globaux installés dans un emplacement personnalisé, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="29642-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="29642-114">Pour répertorier les outils locaux, utilisez l' `--local` option ou omettez les `--global` `--tool-path` options, et `--local` .</span><span class="sxs-lookup"><span data-stu-id="29642-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="29642-115">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="29642-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="29642-116">Options</span><span class="sxs-lookup"><span data-stu-id="29642-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="29642-117">Répertorie les outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="29642-117">Lists user-wide global tools.</span></span> <span data-ttu-id="29642-118">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="29642-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="29642-119">L’omission `--global` de et `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="29642-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="29642-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="29642-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="29642-121">Répertorie les outils locaux pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="29642-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="29642-122">Ne peut pas être combiné avec les `--global` `--tool-path` options ou.</span><span class="sxs-lookup"><span data-stu-id="29642-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="29642-123">L’omission `--global` de et `--tool-path` répertorie les outils locaux même si `--local` n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="29642-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="29642-124">Spécifie un emplacement personnalisé où trouver les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="29642-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="29642-125">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="29642-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="29642-126">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="29642-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="29642-127">L’omission `--global` de et `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="29642-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="29642-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="29642-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="29642-129">Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre ordinateur (profil utilisateur actuel).</span><span class="sxs-lookup"><span data-stu-id="29642-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="29642-130">Répertorie les outils globaux d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="29642-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="29642-131">Répertorie les outils globaux d’un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="29642-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="29642-132">**`dotnet tool list`** ni **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="29642-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="29642-133">Répertorie tous les outils locaux disponibles dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="29642-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="29642-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29642-134">See also</span></span>

- [<span data-ttu-id="29642-135">Outils .NET</span><span class="sxs-lookup"><span data-stu-id="29642-135">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="29642-136">Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="29642-136">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="29642-137">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="29642-137">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
