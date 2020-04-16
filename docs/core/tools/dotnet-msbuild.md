---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463624"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="86eba-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="86eba-103">dotnet msbuild</span></span>

<span data-ttu-id="86eba-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="86eba-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="86eba-105">Nom</span><span class="sxs-lookup"><span data-stu-id="86eba-105">Name</span></span>

<span data-ttu-id="86eba-106">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="86eba-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="86eba-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="86eba-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="86eba-108">Description</span><span class="sxs-lookup"><span data-stu-id="86eba-108">Description</span></span>

<span data-ttu-id="86eba-109">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="86eba-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="86eba-110">La commande a exactement les mêmes capacités que le client de ligne de commande MSBuild existant pour les projets de style SDK seulement.</span><span class="sxs-lookup"><span data-stu-id="86eba-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="86eba-111">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="86eba-111">The options are all the same.</span></span> <span data-ttu-id="86eba-112">Pour plus d’informations sur les options disponibles, consultez la [référence MSBuild de la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="86eba-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="86eba-113">La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="86eba-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="86eba-114">[la construction de dotnet](dotnet-build.md) est plus couramment utilisée pour la construction `dotnet msbuild` de projets, mais parce qu’elle exécute toujours la cible de construction, vous pouvez utiliser lorsque vous ne voulez pas construire le projet.</span><span class="sxs-lookup"><span data-stu-id="86eba-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="86eba-115">Par exemple, si vous avez une cible spécifique que `dotnet msbuild` vous souhaitez exécuter sans construire le projet, utilisez et spécifiez la cible.</span><span class="sxs-lookup"><span data-stu-id="86eba-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="86eba-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="86eba-116">Examples</span></span>

- <span data-ttu-id="86eba-117">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="86eba-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="86eba-118">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="86eba-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="86eba-119">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="86eba-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="86eba-120">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="86eba-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
