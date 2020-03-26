---
title: dotnet nuget supprimer la commande source
description: La commande source de sous-vêtements dotnet supprime une source existante de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148539"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="cda53-103">dotnet nuget supprimer la source</span><span class="sxs-lookup"><span data-stu-id="cda53-103">dotnet nuget remove source</span></span>

<span data-ttu-id="cda53-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cda53-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cda53-105">Nom</span><span class="sxs-lookup"><span data-stu-id="cda53-105">Name</span></span>

<span data-ttu-id="cda53-106">`dotnet nuget remove source`- Supprimer une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="cda53-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cda53-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="cda53-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cda53-108">Description</span><span class="sxs-lookup"><span data-stu-id="cda53-108">Description</span></span>

<span data-ttu-id="cda53-109">La `dotnet nuget remove source` commande supprime une source existante de vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cda53-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="cda53-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="cda53-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="cda53-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="cda53-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="cda53-112">Options</span><span class="sxs-lookup"><span data-stu-id="cda53-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="cda53-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cda53-113">The NuGet configuration file.</span></span> <span data-ttu-id="cda53-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="cda53-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="cda53-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="cda53-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="cda53-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="cda53-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="cda53-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="cda53-117">Examples</span></span>

- <span data-ttu-id="cda53-118">Supprimer une source `mySource`avec le nom de :</span><span class="sxs-lookup"><span data-stu-id="cda53-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="cda53-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cda53-119">See also</span></span>

- [<span data-ttu-id="cda53-120">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="cda53-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="cda53-121">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="cda53-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
