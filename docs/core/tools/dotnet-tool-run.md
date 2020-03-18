---
title: commande d’exécution d’outil de dotnet
description: La commande d’exécution d’outil de dotnet invoque un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847844"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="51461-103">dotnet outil exécuter</span><span class="sxs-lookup"><span data-stu-id="51461-103">dotnet tool run</span></span>

<span data-ttu-id="51461-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="51461-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="51461-105">Nom</span><span class="sxs-lookup"><span data-stu-id="51461-105">Name</span></span>

<span data-ttu-id="51461-106">`dotnet tool run`- Invoque un outil local.</span><span class="sxs-lookup"><span data-stu-id="51461-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="51461-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="51461-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="51461-108">Description</span><span class="sxs-lookup"><span data-stu-id="51461-108">Description</span></span>

<span data-ttu-id="51461-109">L’outil `dotnet tool run` de recherche de commande manifeste les fichiers qui sont en portée pour l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="51461-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="51461-110">Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil.</span><span class="sxs-lookup"><span data-stu-id="51461-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="51461-111">Pour plus d’informations, voir [Invoquez un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="51461-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="51461-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="51461-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="51461-113">Le nom de commande de l’outil à exécuter.</span><span class="sxs-lookup"><span data-stu-id="51461-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="51461-114">Options</span><span class="sxs-lookup"><span data-stu-id="51461-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="51461-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="51461-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="51461-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="51461-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="51461-117">Exécute `dotnetsay` l’outil local.</span><span class="sxs-lookup"><span data-stu-id="51461-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="51461-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51461-118">See also</span></span>

- [<span data-ttu-id="51461-119">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="51461-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="51461-120">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="51461-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
