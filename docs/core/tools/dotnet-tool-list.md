---
title: Commande dotnet tool list
description: La commande de liste d’outils dotnet répertorie les outils .NET Core qui sont installés sur votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: f231dcfe64a925f75f948d508e7a2d83befd9a00
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156983"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="99d5b-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="99d5b-103">dotnet tool list</span></span>

<span data-ttu-id="99d5b-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="99d5b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="99d5b-105">Nom</span><span class="sxs-lookup"><span data-stu-id="99d5b-105">Name</span></span>

<span data-ttu-id="99d5b-106">`dotnet tool list`-répertorie tous les [outils .net Core](global-tools.md) du type spécifié actuellement installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="99d5b-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="99d5b-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="99d5b-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="99d5b-108">Description</span><span class="sxs-lookup"><span data-stu-id="99d5b-108">Description</span></span>

<span data-ttu-id="99d5b-109">La commande `dotnet tool list` vous permet de répertorier tous les outils globaux .NET Core, les outils de chemin d’accès d’outils ou les outils locaux installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="99d5b-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="99d5b-110">La commande répertorie le nom du package, la version installée et la commande d’outil.</span><span class="sxs-lookup"><span data-stu-id="99d5b-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="99d5b-111">Pour utiliser la commande, vous spécifiez l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="99d5b-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="99d5b-112">Outil Global installé à l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="99d5b-112">A global tool installed in the default location.</span></span> <span data-ttu-id="99d5b-113">Utiliser l’option `--global`</span><span class="sxs-lookup"><span data-stu-id="99d5b-113">Use the `--global` option</span></span>
* <span data-ttu-id="99d5b-114">Outil Global installé dans un emplacement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99d5b-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="99d5b-115">Utilisez l'option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="99d5b-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="99d5b-116">Outil local.</span><span class="sxs-lookup"><span data-stu-id="99d5b-116">A local tool.</span></span> <span data-ttu-id="99d5b-117">Omettez les options `--global` et `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="99d5b-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="99d5b-118">**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="99d5b-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="99d5b-119">Options</span><span class="sxs-lookup"><span data-stu-id="99d5b-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="99d5b-120">Répertorie les outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="99d5b-120">Lists user-wide global tools.</span></span> <span data-ttu-id="99d5b-121">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="99d5b-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="99d5b-122">L’omission des `--global` et des `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="99d5b-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="99d5b-123">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="99d5b-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="99d5b-124">Spécifie un emplacement personnalisé où trouver les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="99d5b-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="99d5b-125">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="99d5b-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="99d5b-126">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="99d5b-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="99d5b-127">L’omission des `--global` et des `--tool-path` répertorie les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="99d5b-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="99d5b-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="99d5b-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="99d5b-129">Répertorie tous les outils globaux installés à l’échelle de l’utilisateur sur votre ordinateur (profil utilisateur actuel).</span><span class="sxs-lookup"><span data-stu-id="99d5b-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="99d5b-130">Répertorie les outils globaux d’un répertoire Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="99d5b-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="99d5b-131">Répertorie les outils globaux d’un répertoire Linux/macOS spécifique.</span><span class="sxs-lookup"><span data-stu-id="99d5b-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="99d5b-132">Répertorie tous les outils locaux disponibles dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="99d5b-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="99d5b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99d5b-133">See also</span></span>

- [<span data-ttu-id="99d5b-134">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="99d5b-134">.NET Core tools</span></span>](global-tools.md)
