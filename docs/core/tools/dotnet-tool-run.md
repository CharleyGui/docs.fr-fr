---
title: commande d’exécution d’outil de dotnet
description: La commande d’exécution d’outil de dotnet invoque un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463328"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="950fb-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="950fb-103">dotnet tool run</span></span>

<span data-ttu-id="950fb-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="950fb-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="950fb-105">Nom</span><span class="sxs-lookup"><span data-stu-id="950fb-105">Name</span></span>

<span data-ttu-id="950fb-106">`dotnet tool run`- Invoque un outil local.</span><span class="sxs-lookup"><span data-stu-id="950fb-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="950fb-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="950fb-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="950fb-108">Description</span><span class="sxs-lookup"><span data-stu-id="950fb-108">Description</span></span>

<span data-ttu-id="950fb-109">L’outil `dotnet tool run` de recherche de commande manifeste les fichiers qui sont en portée pour l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="950fb-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="950fb-110">Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil.</span><span class="sxs-lookup"><span data-stu-id="950fb-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="950fb-111">Pour plus d’informations, voir [Invoquez un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="950fb-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="950fb-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="950fb-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="950fb-113">Le nom de commande de l’outil à exécuter.</span><span class="sxs-lookup"><span data-stu-id="950fb-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="950fb-114">Options</span><span class="sxs-lookup"><span data-stu-id="950fb-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="950fb-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="950fb-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="950fb-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="950fb-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="950fb-117">Exécute `dotnetsay` l’outil local.</span><span class="sxs-lookup"><span data-stu-id="950fb-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="950fb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="950fb-118">See also</span></span>

- [<span data-ttu-id="950fb-119">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="950fb-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="950fb-120">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="950fb-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
