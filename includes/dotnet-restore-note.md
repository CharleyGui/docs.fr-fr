---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632110"
---
> [!NOTE]
> <span data-ttu-id="949bd-101">En commençant par .NET Core 2.0 SDK, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) vous n’avez pas à courir parce qu’il est `dotnet new` `dotnet build` géré `dotnet run`implicitement par toutes les commandes qui nécessitent une restauration de se produire, tels que , et .</span><span class="sxs-lookup"><span data-stu-id="949bd-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="949bd-102">Cette commande reste néanmoins valide dans certains scénarios où une restauration explicite est nécessaire, comme des [builds d’intégration continue dans Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment auquel la restauration se produit.</span><span class="sxs-lookup"><span data-stu-id="949bd-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
