---
title: commande dotnet NuGet Remove source
description: La commande dotnet NuGet Remove source supprime une source existante de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537887"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="cfe39-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="cfe39-103">dotnet nuget remove source</span></span>

<span data-ttu-id="cfe39-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cfe39-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cfe39-105">Name</span><span class="sxs-lookup"><span data-stu-id="cfe39-105">Name</span></span>

<span data-ttu-id="cfe39-106">`dotnet nuget remove source` -Supprime une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="cfe39-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfe39-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="cfe39-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a><span data-ttu-id="cfe39-108">Description</span><span class="sxs-lookup"><span data-stu-id="cfe39-108">Description</span></span>

<span data-ttu-id="cfe39-109">La `dotnet nuget remove source` commande supprime une source existante de vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cfe39-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="cfe39-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="cfe39-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="cfe39-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="cfe39-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="cfe39-112">Options</span><span class="sxs-lookup"><span data-stu-id="cfe39-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="cfe39-113">Fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="cfe39-113">The NuGet configuration file.</span></span> <span data-ttu-id="cfe39-114">Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="cfe39-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="cfe39-115">S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="cfe39-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="cfe39-116">Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="cfe39-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="cfe39-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="cfe39-117">Examples</span></span>

- <span data-ttu-id="cfe39-118">Supprimer une source portant le nom `mySource` :</span><span class="sxs-lookup"><span data-stu-id="cfe39-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="cfe39-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfe39-119">See also</span></span>

- [<span data-ttu-id="cfe39-120">Sections sources du package dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="cfe39-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="cfe39-121">sources, commande (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="cfe39-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
