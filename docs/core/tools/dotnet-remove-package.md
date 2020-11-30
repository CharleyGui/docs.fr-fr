---
title: Commande dotnet remove package
description: La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2020
ms.locfileid: "81463455"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="6e34e-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="6e34e-103">dotnet remove package</span></span>

<span data-ttu-id="6e34e-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6e34e-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6e34e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="6e34e-105">Name</span></span>

<span data-ttu-id="6e34e-106">`dotnet remove package` : Supprime une référence de package d’un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6e34e-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6e34e-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6e34e-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="6e34e-108">Description</span><span class="sxs-lookup"><span data-stu-id="6e34e-108">Description</span></span>

<span data-ttu-id="6e34e-109">La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="6e34e-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="6e34e-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e34e-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6e34e-111">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6e34e-111">Specifies the project file.</span></span> <span data-ttu-id="6e34e-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="6e34e-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="6e34e-113">Référence de package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6e34e-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="6e34e-114">Options</span><span class="sxs-lookup"><span data-stu-id="6e34e-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="6e34e-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6e34e-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="6e34e-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="6e34e-116">Examples</span></span>

- <span data-ttu-id="6e34e-117">Supprimer `Newtonsoft.Json` le package NuGet d’un projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="6e34e-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
