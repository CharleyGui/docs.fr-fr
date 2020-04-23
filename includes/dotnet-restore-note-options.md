---
ms.openlocfilehash: 6c04437c2a211b244e6c5eda0893b267c59668e9
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102765"
---
<span data-ttu-id="7872a-101">Vous n’avez pas [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) à courir parce qu’il est géré implicitement par `dotnet new`toutes `dotnet build` `dotnet run`les `dotnet test`commandes qui nécessitent une restauration à se produire, tels que , , , , `dotnet publish`, et `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="7872a-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="7872a-102">Pour désactiver la restauration `--no-restore` implicite, utilisez l’option.</span><span class="sxs-lookup"><span data-stu-id="7872a-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="7872a-103">La `dotnet restore` commande est encore utile dans certains scénarios où la restauration explicite est logique, comme [l’intégration continue s’accumule dans Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de construction qui doivent contrôler explicitement lorsque la restauration se produit.</span><span class="sxs-lookup"><span data-stu-id="7872a-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="7872a-104">Pour plus d’informations sur la façon [ `dotnet restore` ](../docs/core/tools/dotnet-restore.md)de gérer les flux NuGet, consultez la documentation .</span><span class="sxs-lookup"><span data-stu-id="7872a-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>

<span data-ttu-id="7872a-105">Cette commande `dotnet restore` prend en charge les options lorsqu’elle est passée sous la forme longue (par exemple, `--source`).</span><span class="sxs-lookup"><span data-stu-id="7872a-105">This command supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="7872a-106">Les options sous forme abrégée, comme `-s`, ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7872a-106">Short form options, such as `-s`, are not supported.</span></span>
