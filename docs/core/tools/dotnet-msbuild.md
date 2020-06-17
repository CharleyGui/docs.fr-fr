---
title: Commande dotnet msbuild
description: La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803174"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="64dc2-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="64dc2-103">dotnet msbuild</span></span>

<span data-ttu-id="64dc2-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="64dc2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="64dc2-105">Name</span><span class="sxs-lookup"><span data-stu-id="64dc2-105">Name</span></span>

<span data-ttu-id="64dc2-106">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="64dc2-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="64dc2-107">Remarque : vous devrez peut-être spécifier un fichier solution ou projet s’il en existe plusieurs.</span><span class="sxs-lookup"><span data-stu-id="64dc2-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="64dc2-108">Synopsis</span><span class="sxs-lookup"><span data-stu-id="64dc2-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="64dc2-109">Description</span><span class="sxs-lookup"><span data-stu-id="64dc2-109">Description</span></span>

<span data-ttu-id="64dc2-110">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="64dc2-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="64dc2-111">La commande a exactement les mêmes fonctionnalités que le client de ligne de commande MSBuild existant pour les projets de style SDK uniquement.</span><span class="sxs-lookup"><span data-stu-id="64dc2-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="64dc2-112">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="64dc2-112">The options are all the same.</span></span> <span data-ttu-id="64dc2-113">Pour plus d’informations sur les options disponibles, consultez la page de référence de la [ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="64dc2-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="64dc2-114">La commande [dotnet build](dotnet-build.md) est équivalente à `dotnet msbuild -restore`.</span><span class="sxs-lookup"><span data-stu-id="64dc2-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="64dc2-115">Lorsque vous ne souhaitez pas générer le projet et que vous avez une cible spécifique que vous souhaitez exécuter, utilisez `dotnet build` ou `dotnet msbuild` et spécifiez la cible.</span><span class="sxs-lookup"><span data-stu-id="64dc2-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="64dc2-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="64dc2-116">Examples</span></span>

- <span data-ttu-id="64dc2-117">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="64dc2-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="64dc2-118">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="64dc2-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="64dc2-119">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="64dc2-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="64dc2-120">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="64dc2-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
