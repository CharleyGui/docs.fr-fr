---
title: Commande dotnet nuget locals
description: La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 482e841d3b402084eb8c7f2456779f1600a5dd19
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117620"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="44f76-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="44f76-103">dotnet nuget locals</span></span>

<span data-ttu-id="44f76-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="44f76-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="44f76-105">Name</span><span class="sxs-lookup"><span data-stu-id="44f76-105">Name</span></span>

<span data-ttu-id="44f76-106">`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.</span><span class="sxs-lookup"><span data-stu-id="44f76-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="44f76-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="44f76-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="44f76-108">Description</span><span class="sxs-lookup"><span data-stu-id="44f76-108">Description</span></span>

<span data-ttu-id="44f76-109">La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44f76-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="44f76-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="44f76-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="44f76-111">Emplacement du cache à répertorier ou effacer.</span><span class="sxs-lookup"><span data-stu-id="44f76-111">The cache location to list or clear.</span></span> <span data-ttu-id="44f76-112">L’une des valeurs suivantes est acceptée :</span><span class="sxs-lookup"><span data-stu-id="44f76-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="44f76-113">`all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="44f76-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="44f76-114">`http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="44f76-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="44f76-115">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="44f76-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="44f76-116">`global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux.</span><span class="sxs-lookup"><span data-stu-id="44f76-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="44f76-117">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="44f76-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="44f76-118">`temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="44f76-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="44f76-119">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="44f76-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="44f76-120">Options</span><span class="sxs-lookup"><span data-stu-id="44f76-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="44f76-121">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="44f76-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="44f76-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="44f76-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="44f76-123">L’option clear exécute une opération d’effacement sur le type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="44f76-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="44f76-124">Le contenu des répertoires de cache est supprimé de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="44f76-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="44f76-125">Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache.</span><span class="sxs-lookup"><span data-stu-id="44f76-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="44f76-126">Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.</span><span class="sxs-lookup"><span data-stu-id="44f76-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="44f76-127">L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="44f76-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="44f76-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="44f76-128">Examples</span></span>

* <span data-ttu-id="44f76-129">Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="44f76-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="44f76-130">Affiche le chemin du répertoire du cache http local :</span><span class="sxs-lookup"><span data-stu-id="44f76-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="44f76-131">Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="44f76-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="44f76-132">Effacer tous les fichiers du répertoire du cache des packages globaux local :</span><span class="sxs-lookup"><span data-stu-id="44f76-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="44f76-133">Effacer tous les fichiers du répertoire du cache temporaire local :</span><span class="sxs-lookup"><span data-stu-id="44f76-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="44f76-134">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="44f76-134">Troubleshooting</span></span>

<span data-ttu-id="44f76-135">Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="44f76-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
