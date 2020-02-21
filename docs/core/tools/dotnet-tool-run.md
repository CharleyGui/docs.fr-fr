---
title: commande d’exécution de l’outil dotnet
description: La commande d’exécution de l’outil dotnet appelle un outil local.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543879"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="5f728-103">exécution de l’outil dotnet</span><span class="sxs-lookup"><span data-stu-id="5f728-103">dotnet tool run</span></span>

<span data-ttu-id="5f728-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5f728-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5f728-105">Name</span><span class="sxs-lookup"><span data-stu-id="5f728-105">Name</span></span>

<span data-ttu-id="5f728-106">`dotnet tool run` : appelle un outil local.</span><span class="sxs-lookup"><span data-stu-id="5f728-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f728-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5f728-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5f728-108">Description</span><span class="sxs-lookup"><span data-stu-id="5f728-108">Description</span></span>

<span data-ttu-id="5f728-109">La commande `dotnet tool run` recherche les fichiers de manifeste de l’outil qui se trouvent dans la portée du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5f728-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="5f728-110">Lorsqu’il trouve une référence à l’outil spécifié, il exécute l’outil.</span><span class="sxs-lookup"><span data-stu-id="5f728-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="5f728-111">Pour plus d’informations, consultez [appeler un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="5f728-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="5f728-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f728-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="5f728-113">Nom de commande de l’outil à exécuter.</span><span class="sxs-lookup"><span data-stu-id="5f728-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="5f728-114">Options</span><span class="sxs-lookup"><span data-stu-id="5f728-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5f728-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5f728-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="5f728-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f728-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="5f728-117">Exécute l’outil local `dotnetsay`.</span><span class="sxs-lookup"><span data-stu-id="5f728-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f728-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f728-118">See also</span></span>

- [<span data-ttu-id="5f728-119">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f728-119">.NET Core tools</span></span>](global-tools.md)
