---
title: dotnet nuget liste source commande
description: La commande source de la liste de négget dotnet répertorie toutes les sources existantes de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148574"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="87702-103">dotnet nuget liste source</span><span class="sxs-lookup"><span data-stu-id="87702-103">dotnet nuget list source</span></span>

<span data-ttu-id="87702-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="87702-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="87702-105">Nom</span><span class="sxs-lookup"><span data-stu-id="87702-105">Name</span></span>

<span data-ttu-id="87702-106">`dotnet nuget list source`- Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="87702-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87702-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="87702-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="87702-108">Description</span><span class="sxs-lookup"><span data-stu-id="87702-108">Description</span></span>

<span data-ttu-id="87702-109">La `dotnet nuget list source` commande répertorie toutes les sources existantes de vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="87702-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="87702-110">Options</span><span class="sxs-lookup"><span data-stu-id="87702-110">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="87702-111">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="87702-111">The NuGet configuration file.</span></span> <span data-ttu-id="87702-112">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="87702-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="87702-113">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="87702-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="87702-114">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="87702-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format`**

  <span data-ttu-id="87702-115">Le format de la `Detailed` sortie de commande `Short`de liste : (la valeur par défaut) et .</span><span class="sxs-lookup"><span data-stu-id="87702-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="87702-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="87702-116">Examples</span></span>

- <span data-ttu-id="87702-117">Liste des sources configurées de l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="87702-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="87702-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87702-118">See also</span></span>

- [<span data-ttu-id="87702-119">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="87702-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="87702-120">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="87702-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
