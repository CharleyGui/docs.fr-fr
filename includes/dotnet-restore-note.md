---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102738"
---
<span data-ttu-id="a44fc-101">Vous n’avez pas à exécuter [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , car il est exécuté implicitement par toutes les commandes qui nécessitent une restauration, comme,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` et `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="a44fc-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="a44fc-102">Pour désactiver la restauration implicite, utilisez l' `--no-restore` option.</span><span class="sxs-lookup"><span data-stu-id="a44fc-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="a44fc-103">La `dotnet restore` commande est toujours utile dans certains scénarios où la restauration explicite est appropriée, comme les [Builds d’intégration continue dans Azure DevOps services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment où la restauration se produit.</span><span class="sxs-lookup"><span data-stu-id="a44fc-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="a44fc-104">Pour plus d’informations sur la gestion des flux NuGet, consultez la [ `dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="a44fc-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
