---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537732"
---
<span data-ttu-id="9de88-101">Vous n’avez pas à exécuter [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , car il est exécuté implicitement par toutes les commandes qui nécessitent une restauration, comme,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` et `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="9de88-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="9de88-102">Pour désactiver la restauration implicite, utilisez l' `--no-restore` option.</span><span class="sxs-lookup"><span data-stu-id="9de88-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="9de88-103">La `dotnet restore` commande est toujours utile dans certains scénarios où la restauration explicite est appropriée, comme les [Builds d’intégration continue dans Azure DevOps services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment où la restauration se produit.</span><span class="sxs-lookup"><span data-stu-id="9de88-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="9de88-104">Pour plus d’informations sur la gestion des flux NuGet, consultez la [ `dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="9de88-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
