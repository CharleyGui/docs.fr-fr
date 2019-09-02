---
title: Commande dotnet nuget locals
description: La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0cf025f91a7582fafc401799cd1d8b933b087535
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202468"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="89f98-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="89f98-103">dotnet nuget locals</span></span>

<span data-ttu-id="89f98-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="89f98-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="89f98-105">Name</span><span class="sxs-lookup"><span data-stu-id="89f98-105">Name</span></span>

<span data-ttu-id="89f98-106">`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.</span><span class="sxs-lookup"><span data-stu-id="89f98-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="89f98-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="89f98-107">Synopsis</span></span>

```console
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="89f98-108">Description</span><span class="sxs-lookup"><span data-stu-id="89f98-108">Description</span></span>

<span data-ttu-id="89f98-109">La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89f98-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="89f98-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="89f98-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="89f98-111">Emplacement du cache à répertorier ou effacer.</span><span class="sxs-lookup"><span data-stu-id="89f98-111">The cache location to list or clear.</span></span> <span data-ttu-id="89f98-112">L’une des valeurs suivantes est acceptée :</span><span class="sxs-lookup"><span data-stu-id="89f98-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="89f98-113">`all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="89f98-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="89f98-114">`http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="89f98-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="89f98-115">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="89f98-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="89f98-116">`global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux.</span><span class="sxs-lookup"><span data-stu-id="89f98-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="89f98-117">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="89f98-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="89f98-118">`temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="89f98-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="89f98-119">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="89f98-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="89f98-120">Options</span><span class="sxs-lookup"><span data-stu-id="89f98-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="89f98-121">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="89f98-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="89f98-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="89f98-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="89f98-123">L’option clear exécute une opération d’effacement sur le type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="89f98-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="89f98-124">Le contenu des répertoires de cache est supprimé de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="89f98-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="89f98-125">Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache.</span><span class="sxs-lookup"><span data-stu-id="89f98-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="89f98-126">Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.</span><span class="sxs-lookup"><span data-stu-id="89f98-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="89f98-127">L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="89f98-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="89f98-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="89f98-128">Examples</span></span>

* <span data-ttu-id="89f98-129">Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="89f98-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="89f98-130">Affiche le chemin du répertoire du cache http local :</span><span class="sxs-lookup"><span data-stu-id="89f98-130">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="89f98-131">Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="89f98-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="89f98-132">Effacer tous les fichiers du répertoire du cache des packages globaux local :</span><span class="sxs-lookup"><span data-stu-id="89f98-132">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="89f98-133">Effacer tous les fichiers du répertoire du cache temporaire local :</span><span class="sxs-lookup"><span data-stu-id="89f98-133">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="89f98-134">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="89f98-134">Troubleshooting</span></span>

<span data-ttu-id="89f98-135">Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="89f98-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
