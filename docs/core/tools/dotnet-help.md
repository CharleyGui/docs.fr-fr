---
title: Commande dotnet help
description: La commande dotnet help affiche une documentation en ligne plus détaillée pour la commande spécifiée.
ms.date: 02/14/2020
ms.openlocfilehash: d583142edabb24df972bdf9a06dbfe04688f9d97
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634466"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="bc124-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="bc124-103">dotnet help reference</span></span>

<span data-ttu-id="bc124-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bc124-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bc124-105">Name</span><span class="sxs-lookup"><span data-stu-id="bc124-105">Name</span></span>

<span data-ttu-id="bc124-106">`dotnet help` : affiche une documentation en ligne plus détaillée pour la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bc124-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc124-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bc124-107">Synopsis</span></span>

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="bc124-108">Description</span><span class="sxs-lookup"><span data-stu-id="bc124-108">Description</span></span>

<span data-ttu-id="bc124-109">La commande `dotnet help` ouvre la page de référence sur docs.microsoft.com pour afficher des informations plus détaillées sur la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bc124-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="bc124-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="bc124-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="bc124-111">Nom de la commande CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="bc124-111">Name of the .NET CLI command.</span></span> <span data-ttu-id="bc124-112">Pour obtenir la liste des commandes CLI valides, consultez [Commandes CLI](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="bc124-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="bc124-113">Options</span><span class="sxs-lookup"><span data-stu-id="bc124-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="bc124-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="bc124-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="bc124-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="bc124-115">Examples</span></span>

- <span data-ttu-id="bc124-116">Ouvre la page de documentation de la commande [dotnet new](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="bc124-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
