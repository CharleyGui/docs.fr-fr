---
title: dotnet nuget désactiver la commande source
description: La commande source désactivable de dotnet désactive une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 5aa16c842bcddeead180fdeec3d9dcdda33f7ed9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148553"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="efce6-103">dotnet nuget source désactiver</span><span class="sxs-lookup"><span data-stu-id="efce6-103">dotnet nuget disable source</span></span>

<span data-ttu-id="efce6-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="efce6-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="efce6-105">Nom</span><span class="sxs-lookup"><span data-stu-id="efce6-105">Name</span></span>

<span data-ttu-id="efce6-106">`dotnet nuget disable source`- Désactiver une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="efce6-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="efce6-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="efce6-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile]
dotnet nuget disable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="efce6-108">Description</span><span class="sxs-lookup"><span data-stu-id="efce6-108">Description</span></span>

<span data-ttu-id="efce6-109">La `dotnet nuget disable source` commande désactive une source existante dans vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="efce6-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="efce6-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="efce6-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="efce6-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="efce6-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="efce6-112">Options</span><span class="sxs-lookup"><span data-stu-id="efce6-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="efce6-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="efce6-113">The NuGet configuration file.</span></span> <span data-ttu-id="efce6-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="efce6-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="efce6-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="efce6-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="efce6-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="efce6-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="efce6-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="efce6-117">Examples</span></span>

- <span data-ttu-id="efce6-118">Désactiver une source avec `mySource`le nom de :</span><span class="sxs-lookup"><span data-stu-id="efce6-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="efce6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efce6-119">See also</span></span>

- [<span data-ttu-id="efce6-120">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="efce6-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="efce6-121">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="efce6-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
