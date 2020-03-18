---
title: Commande dotnet remove package
description: La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503634"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="7893f-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="7893f-103">dotnet remove package</span></span>

<span data-ttu-id="7893f-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="7893f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7893f-105">Nom</span><span class="sxs-lookup"><span data-stu-id="7893f-105">Name</span></span>

<span data-ttu-id="7893f-106">`dotnet remove package` : Supprime une référence de package d’un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="7893f-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7893f-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="7893f-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7893f-108">Description</span><span class="sxs-lookup"><span data-stu-id="7893f-108">Description</span></span>

<span data-ttu-id="7893f-109">La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="7893f-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="7893f-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="7893f-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7893f-111">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="7893f-111">Specifies the project file.</span></span> <span data-ttu-id="7893f-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="7893f-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="7893f-113">Référence de package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="7893f-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="7893f-114">Options</span><span class="sxs-lookup"><span data-stu-id="7893f-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7893f-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="7893f-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="7893f-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="7893f-116">Examples</span></span>

- <span data-ttu-id="7893f-117">Supprimer `Newtonsoft.Json` le paquet NuGet d’un projet dans l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="7893f-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
