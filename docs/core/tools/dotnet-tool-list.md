---
title: Commande dotnet tool list
description: La commande dotnet tool list répertorie l’outil global .NET Core spécifié à partir de votre machine.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117559"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="6f184-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="6f184-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="6f184-104">Name</span><span class="sxs-lookup"><span data-stu-id="6f184-104">Name</span></span>

<span data-ttu-id="6f184-105">`dotnet tool list` - Répertorie tous les [outils globaux .NET Core](global-tools.md) actuellement installés dans le répertoire par défaut de votre machine ou à l’emplacement du chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f184-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6f184-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="6f184-106">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="6f184-107">Description</span><span class="sxs-lookup"><span data-stu-id="6f184-107">Description</span></span>

<span data-ttu-id="6f184-108">La commande `dotnet tool list` vous offre un moyen de lister tous les outils globaux .NET Core installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel) ou à l’emplacement du chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f184-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="6f184-109">La commande liste le nom du package, la version installée et la commande de l’outil global.</span><span class="sxs-lookup"><span data-stu-id="6f184-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="6f184-110">Pour utiliser cette commande, vous devez soit indiquer que vous voulez voir tous les outils à l’échelle de l’utilisateur à l’aide de l’option `--global`, soit spécifier un chemin personnalisé à l’aide de l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="6f184-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="6f184-111">Options</span><span class="sxs-lookup"><span data-stu-id="6f184-111">Options</span></span>

`-g|--global`

<span data-ttu-id="6f184-112">Liste les outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f184-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="6f184-113">Non combinable avec l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="6f184-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="6f184-114">Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="6f184-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="6f184-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6f184-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="6f184-116">Spécifie un emplacement personnalisé où trouver les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="6f184-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="6f184-117">Le chemin peut être absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="6f184-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="6f184-118">Non combinable avec l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="6f184-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="6f184-119">Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--global`.</span><span class="sxs-lookup"><span data-stu-id="6f184-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="6f184-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="6f184-120">Examples</span></span>

<span data-ttu-id="6f184-121">Liste tous les outils globaux installés à l’échelle de l’utilisateur sur votre machine (profil utilisateur actuel) :</span><span class="sxs-lookup"><span data-stu-id="6f184-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="6f184-122">Liste les outils globaux à partir d’un dossier Windows spécifique :</span><span class="sxs-lookup"><span data-stu-id="6f184-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="6f184-123">Liste les outils globaux à partir d’un dossier Linux/macOS spécifique :</span><span class="sxs-lookup"><span data-stu-id="6f184-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="6f184-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f184-124">See also</span></span>

- [<span data-ttu-id="6f184-125">Outils globaux .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f184-125">.NET Core Global Tools</span></span>](global-tools.md)
