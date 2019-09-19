---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117704"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="2f5f0-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2f5f0-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2f5f0-104">Name</span><span class="sxs-lookup"><span data-stu-id="2f5f0-104">Name</span></span>

<span data-ttu-id="2f5f0-105">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f5f0-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="2f5f0-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="2f5f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="2f5f0-107">Description</span></span>

<span data-ttu-id="2f5f0-108">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="2f5f0-109">La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour un projet de type SDK uniquement.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="2f5f0-110">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-110">The options are all the same.</span></span> <span data-ttu-id="2f5f0-111">Pour plus d’informations sur les options disponibles, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="2f5f0-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="2f5f0-112">La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="2f5f0-113">`dotnet build` est généralement utilisée pour générer les projets, mais `dotnet msbuild` vous donne davantage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="2f5f0-114">Par exemple, si vous avez une cible spécifique que vous souhaitez exécuter (sans exécuter la cible build ), utilisez plutôt `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="2f5f0-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="2f5f0-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f5f0-115">Examples</span></span>

* <span data-ttu-id="2f5f0-116">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="2f5f0-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="2f5f0-117">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="2f5f0-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="2f5f0-118">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="2f5f0-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="2f5f0-119">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="2f5f0-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```
