---
title: Commande dotnet help
description: La commande dotnet help affiche une documentation en ligne plus détaillée pour la commande spécifiée.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734231"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="9f328-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="9f328-103">dotnet help reference</span></span>

<span data-ttu-id="9f328-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9f328-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="9f328-105">Nom</span><span class="sxs-lookup"><span data-stu-id="9f328-105">Name</span></span>

<span data-ttu-id="9f328-106">`dotnet help` : affiche une documentation en ligne plus détaillée pour la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f328-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f328-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="9f328-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="9f328-108">Description</span><span class="sxs-lookup"><span data-stu-id="9f328-108">Description</span></span>

<span data-ttu-id="9f328-109">La commande `dotnet help` ouvre la page de référence sur docs.microsoft.com pour afficher des informations plus détaillées sur la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f328-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="9f328-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f328-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="9f328-111">Nom de la commande CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f328-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="9f328-112">Pour obtenir la liste des commandes CLI valides, consultez [Commandes CLI](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="9f328-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="9f328-113">Options</span><span class="sxs-lookup"><span data-stu-id="9f328-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="9f328-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="9f328-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9f328-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="9f328-115">Examples</span></span>

* <span data-ttu-id="9f328-116">Ouvre la page de documentation de la commande [dotnet new](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="9f328-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
