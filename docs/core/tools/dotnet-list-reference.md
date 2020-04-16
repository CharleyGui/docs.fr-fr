---
title: Commande dotnet list reference
description: La commande dotnet list reference est une option pratique pour lister des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463646"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="303d8-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="303d8-103">dotnet list reference</span></span>

<span data-ttu-id="303d8-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="303d8-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="303d8-105">Nom</span><span class="sxs-lookup"><span data-stu-id="303d8-105">Name</span></span>

<span data-ttu-id="303d8-106">`dotnet list reference` : répertorie des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="303d8-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="303d8-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="303d8-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="303d8-108">Description</span><span class="sxs-lookup"><span data-stu-id="303d8-108">Description</span></span>

<span data-ttu-id="303d8-109">La commande `dotnet list reference` est pratique pour lister les références à un projet ou à une solution donné.</span><span class="sxs-lookup"><span data-stu-id="303d8-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="303d8-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="303d8-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="303d8-111">Spécifie le fichier projet ou le fichier solution à utiliser pour lister les références.</span><span class="sxs-lookup"><span data-stu-id="303d8-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="303d8-112">Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="303d8-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="303d8-113">Options</span><span class="sxs-lookup"><span data-stu-id="303d8-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="303d8-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="303d8-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="303d8-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="303d8-115">Examples</span></span>

* <span data-ttu-id="303d8-116">Lister les références de projet pour le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="303d8-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="303d8-117">Lister les références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="303d8-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
