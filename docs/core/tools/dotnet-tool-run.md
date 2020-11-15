---
title: commande d’exécution de l’outil dotnet
description: La commande d’exécution de l’outil dotnet appelle un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634153"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="169ea-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="169ea-103">dotnet tool run</span></span>

<span data-ttu-id="169ea-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="169ea-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="169ea-105">Name</span><span class="sxs-lookup"><span data-stu-id="169ea-105">Name</span></span>

<span data-ttu-id="169ea-106">`dotnet tool run` -Appelle un outil local.</span><span class="sxs-lookup"><span data-stu-id="169ea-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="169ea-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="169ea-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="169ea-108">Description</span><span class="sxs-lookup"><span data-stu-id="169ea-108">Description</span></span>

<span data-ttu-id="169ea-109">La `dotnet tool run` commande recherche les fichiers de manifeste de l’outil qui sont dans la portée du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="169ea-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="169ea-110">Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil.</span><span class="sxs-lookup"><span data-stu-id="169ea-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="169ea-111">Pour plus d’informations, consultez [appeler un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="169ea-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="169ea-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="169ea-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="169ea-113">Nom de commande de l’outil à exécuter.</span><span class="sxs-lookup"><span data-stu-id="169ea-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="169ea-114">Options</span><span class="sxs-lookup"><span data-stu-id="169ea-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="169ea-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="169ea-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="169ea-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="169ea-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="169ea-117">Exécute l' `dotnetsay` outil local.</span><span class="sxs-lookup"><span data-stu-id="169ea-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="169ea-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="169ea-118">See also</span></span>

- [<span data-ttu-id="169ea-119">Outils .NET</span><span class="sxs-lookup"><span data-stu-id="169ea-119">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="169ea-120">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="169ea-120">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
