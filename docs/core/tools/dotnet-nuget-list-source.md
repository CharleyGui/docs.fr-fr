---
title: dotnet nuget liste source commande
description: La commande source de la liste de négget dotnet répertorie toutes les sources existantes de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463540"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="cfc04-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="cfc04-103">dotnet nuget list source</span></span>

<span data-ttu-id="cfc04-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cfc04-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cfc04-105">Nom</span><span class="sxs-lookup"><span data-stu-id="cfc04-105">Name</span></span>

<span data-ttu-id="cfc04-106">`dotnet nuget list source`- Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="cfc04-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfc04-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="cfc04-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="cfc04-108">Description</span><span class="sxs-lookup"><span data-stu-id="cfc04-108">Description</span></span>

<span data-ttu-id="cfc04-109">La `dotnet nuget list source` commande répertorie toutes les sources existantes de vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cfc04-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="cfc04-110">Options</span><span class="sxs-lookup"><span data-stu-id="cfc04-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="cfc04-111">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cfc04-111">The NuGet configuration file.</span></span> <span data-ttu-id="cfc04-112">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="cfc04-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="cfc04-113">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="cfc04-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="cfc04-114">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="cfc04-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="cfc04-115">Le format de la `Detailed` sortie de commande `Short`de liste : (la valeur par défaut) et .</span><span class="sxs-lookup"><span data-stu-id="cfc04-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="cfc04-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="cfc04-116">Examples</span></span>

- <span data-ttu-id="cfc04-117">Liste des sources configurées de l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="cfc04-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="cfc04-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfc04-118">See also</span></span>

- [<span data-ttu-id="cfc04-119">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="cfc04-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="cfc04-120">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="cfc04-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
