---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179987"
---
> [!NOTE]
> <span data-ttu-id="cdc3c-101">En commençant par .NET Core 2.0, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) vous n’avez pas à courir parce qu’il est `dotnet build` exécuté `dotnet run`implicitement par toutes les commandes qui nécessitent une restauration pour se produire, tels que et .</span><span class="sxs-lookup"><span data-stu-id="cdc3c-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="cdc3c-102">Cette commande reste néanmoins valide dans certains scénarios où une restauration explicite est nécessaire, comme des [builds d’intégration continue dans Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment auquel la restauration se produit.</span><span class="sxs-lookup"><span data-stu-id="cdc3c-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="cdc3c-103">Cette commande prend également en charge les options de `dotnet restore` quand elles sont passées sous leur forme longue (par exemple `--source`).</span><span class="sxs-lookup"><span data-stu-id="cdc3c-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="cdc3c-104">Les options sous forme abrégée, comme `-s`, ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cdc3c-104">Short form options, such as `-s`, are not supported.</span></span>
