---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421828"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="2a609-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="2a609-103">dotnet list reference</span></span>

<span data-ttu-id="2a609-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="2a609-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="2a609-105">Name</span><span class="sxs-lookup"><span data-stu-id="2a609-105">Name</span></span>

<span data-ttu-id="2a609-106">`dotnet list reference` : répertorie des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="2a609-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a609-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="2a609-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="2a609-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a609-108">Description</span></span>

<span data-ttu-id="2a609-109">La commande `dotnet list reference` est pratique pour lister les références à un projet ou à une solution donné.</span><span class="sxs-lookup"><span data-stu-id="2a609-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="2a609-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="2a609-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="2a609-111">Spécifie le fichier projet ou le fichier solution à utiliser pour lister les références.</span><span class="sxs-lookup"><span data-stu-id="2a609-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="2a609-112">Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2a609-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="2a609-113">Options</span><span class="sxs-lookup"><span data-stu-id="2a609-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="2a609-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2a609-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2a609-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="2a609-115">Examples</span></span>

* <span data-ttu-id="2a609-116">Lister les références de projet pour le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="2a609-116">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="2a609-117">Lister les références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="2a609-117">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
