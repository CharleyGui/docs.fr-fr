---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733224"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="1407c-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="1407c-103">dotnet list reference</span></span>

<span data-ttu-id="1407c-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1407c-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="1407c-105">Name</span><span class="sxs-lookup"><span data-stu-id="1407c-105">Name</span></span>

<span data-ttu-id="1407c-106">`dotnet list reference` : répertorie des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="1407c-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1407c-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="1407c-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="1407c-108">Description</span><span class="sxs-lookup"><span data-stu-id="1407c-108">Description</span></span>

<span data-ttu-id="1407c-109">La commande `dotnet list reference` est pratique pour lister les références à un projet ou à une solution donné.</span><span class="sxs-lookup"><span data-stu-id="1407c-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="1407c-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="1407c-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="1407c-111">Spécifie le fichier projet ou le fichier solution à utiliser pour lister les références.</span><span class="sxs-lookup"><span data-stu-id="1407c-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="1407c-112">Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="1407c-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="1407c-113">Options</span><span class="sxs-lookup"><span data-stu-id="1407c-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="1407c-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1407c-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1407c-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="1407c-115">Examples</span></span>

* <span data-ttu-id="1407c-116">Lister les références de projet pour le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="1407c-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="1407c-117">Lister les références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="1407c-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
