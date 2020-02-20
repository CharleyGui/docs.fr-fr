---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503678"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="101ce-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="101ce-103">dotnet msbuild</span></span>

<span data-ttu-id="101ce-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="101ce-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="101ce-105">Name</span><span class="sxs-lookup"><span data-stu-id="101ce-105">Name</span></span>

<span data-ttu-id="101ce-106">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="101ce-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="101ce-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="101ce-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="101ce-108">Description</span><span class="sxs-lookup"><span data-stu-id="101ce-108">Description</span></span>

<span data-ttu-id="101ce-109">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="101ce-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="101ce-110">La commande a exactement les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour les projets de style SDK uniquement.</span><span class="sxs-lookup"><span data-stu-id="101ce-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="101ce-111">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="101ce-111">The options are all the same.</span></span> <span data-ttu-id="101ce-112">Pour plus d’informations sur les options disponibles, consultez la page de référence de la [ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="101ce-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="101ce-113">La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="101ce-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="101ce-114">la [génération dotnet](dotnet-build.md) est plus couramment utilisée pour générer des projets, mais parce qu’elle exécute toujours la cible Build, vous pouvez utiliser `dotnet msbuild` lorsque vous ne voulez pas générer le projet.</span><span class="sxs-lookup"><span data-stu-id="101ce-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="101ce-115">Par exemple, si vous avez une cible spécifique que vous souhaitez exécuter sans générer le projet, utilisez `dotnet msbuild` et spécifiez la cible.</span><span class="sxs-lookup"><span data-stu-id="101ce-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="101ce-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="101ce-116">Examples</span></span>

- <span data-ttu-id="101ce-117">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="101ce-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="101ce-118">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="101ce-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="101ce-119">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="101ce-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="101ce-120">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="101ce-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
