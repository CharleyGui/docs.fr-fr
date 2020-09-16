---
title: commande dotnet de la liste de listes NuGet NuGet
description: La commande dotnet NuGet List source répertorie toutes les sources existantes de vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537891"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="ec311-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="ec311-103">dotnet nuget list source</span></span>

<span data-ttu-id="ec311-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ec311-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ec311-105">Name</span><span class="sxs-lookup"><span data-stu-id="ec311-105">Name</span></span>

<span data-ttu-id="ec311-106">`dotnet nuget list source` -Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="ec311-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ec311-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ec311-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="ec311-108">Description</span><span class="sxs-lookup"><span data-stu-id="ec311-108">Description</span></span>

<span data-ttu-id="ec311-109">La `dotnet nuget list source` commande répertorie toutes les sources existantes de vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="ec311-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="ec311-110">Options</span><span class="sxs-lookup"><span data-stu-id="ec311-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="ec311-111">Fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="ec311-111">The NuGet configuration file.</span></span> <span data-ttu-id="ec311-112">Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="ec311-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="ec311-113">S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="ec311-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="ec311-114">Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="ec311-114">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="ec311-115">Format de la sortie de la commande list : `Detailed` (valeur par défaut) et `Short` .</span><span class="sxs-lookup"><span data-stu-id="ec311-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="ec311-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="ec311-116">Examples</span></span>

- <span data-ttu-id="ec311-117">Répertorier les sources configurées à partir du répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="ec311-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="ec311-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec311-118">See also</span></span>

- [<span data-ttu-id="ec311-119">Sections sources du package dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="ec311-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="ec311-120">sources, commande (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="ec311-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
