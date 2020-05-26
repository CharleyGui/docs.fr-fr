---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802765"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="cfc4d-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="cfc4d-103">dotnet list reference</span></span>

<span data-ttu-id="cfc4d-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cfc4d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cfc4d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="cfc4d-105">Name</span></span>

<span data-ttu-id="cfc4d-106">`dotnet list reference` : répertorie des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="cfc4d-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfc4d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="cfc4d-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="cfc4d-108">Description</span><span class="sxs-lookup"><span data-stu-id="cfc4d-108">Description</span></span>

<span data-ttu-id="cfc4d-109">La commande `dotnet list reference` est une option pratique pour répertorier des références de projet pour un projet donné.</span><span class="sxs-lookup"><span data-stu-id="cfc4d-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cfc4d-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="cfc4d-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="cfc4d-111">Fichier projet à traiter.</span><span class="sxs-lookup"><span data-stu-id="cfc4d-111">The project file to operate on.</span></span> <span data-ttu-id="cfc4d-112">Si aucun fichier n’est spécifié, la commande effectue une recherche dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="cfc4d-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="cfc4d-113">Options</span><span class="sxs-lookup"><span data-stu-id="cfc4d-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="cfc4d-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="cfc4d-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="cfc4d-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="cfc4d-115">Examples</span></span>

* <span data-ttu-id="cfc4d-116">Lister les références de projet pour le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="cfc4d-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="cfc4d-117">Lister les références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="cfc4d-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
