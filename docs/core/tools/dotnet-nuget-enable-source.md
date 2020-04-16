---
title: dotnet nuget activer la commande source
description: La commande de source d’activation de négète dotnet permet une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463560"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="8827d-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="8827d-103">dotnet nuget enable source</span></span>

<span data-ttu-id="8827d-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8827d-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8827d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="8827d-105">Name</span></span>

<span data-ttu-id="8827d-106">`dotnet nuget enable source`- Activez une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="8827d-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8827d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8827d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="8827d-108">Description</span><span class="sxs-lookup"><span data-stu-id="8827d-108">Description</span></span>

<span data-ttu-id="8827d-109">La `dotnet nuget enable source` commande permet une source existante dans vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="8827d-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="8827d-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="8827d-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="8827d-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="8827d-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="8827d-112">Options</span><span class="sxs-lookup"><span data-stu-id="8827d-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="8827d-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="8827d-113">The NuGet configuration file.</span></span> <span data-ttu-id="8827d-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="8827d-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="8827d-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="8827d-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="8827d-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="8827d-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="8827d-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="8827d-117">Examples</span></span>

- <span data-ttu-id="8827d-118">Activez une source `mySource`avec le nom de :</span><span class="sxs-lookup"><span data-stu-id="8827d-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="8827d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8827d-119">See also</span></span>

- [<span data-ttu-id="8827d-120">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="8827d-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="8827d-121">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="8827d-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
