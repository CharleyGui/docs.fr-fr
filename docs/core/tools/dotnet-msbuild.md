---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733200"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="aa710-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="aa710-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="aa710-104">Nom</span><span class="sxs-lookup"><span data-stu-id="aa710-104">Name</span></span>

<span data-ttu-id="aa710-105">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="aa710-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aa710-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="aa710-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="aa710-107">Description</span><span class="sxs-lookup"><span data-stu-id="aa710-107">Description</span></span>

<span data-ttu-id="aa710-108">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="aa710-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="aa710-109">La commande a exactement les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour les projets de style SDK uniquement.</span><span class="sxs-lookup"><span data-stu-id="aa710-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="aa710-110">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="aa710-110">The options are all the same.</span></span> <span data-ttu-id="aa710-111">Pour plus d’informations sur les options disponibles, consultez la page de référence de la [ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="aa710-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="aa710-112">La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="aa710-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="aa710-113">la [génération dotnet](dotnet-build.md) est plus couramment utilisée pour générer des projets, mais parce qu’elle exécute toujours la cible Build, vous pouvez utiliser `dotnet msbuild` lorsque vous ne voulez pas générer le projet.</span><span class="sxs-lookup"><span data-stu-id="aa710-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="aa710-114">Par exemple, si vous avez une cible spécifique que vous souhaitez exécuter sans générer le projet, utilisez `dotnet msbuild` et spécifiez la cible.</span><span class="sxs-lookup"><span data-stu-id="aa710-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="aa710-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="aa710-115">Examples</span></span>

* <span data-ttu-id="aa710-116">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="aa710-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="aa710-117">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="aa710-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="aa710-118">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="aa710-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="aa710-119">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="aa710-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
