---
title: Commande dotnet nuget locals
description: La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503686"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="42429-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="42429-103">dotnet nuget locals</span></span>

<span data-ttu-id="42429-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="42429-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="42429-105">Nom</span><span class="sxs-lookup"><span data-stu-id="42429-105">Name</span></span>

<span data-ttu-id="42429-106">`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.</span><span class="sxs-lookup"><span data-stu-id="42429-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="42429-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="42429-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="42429-108">Description</span><span class="sxs-lookup"><span data-stu-id="42429-108">Description</span></span>

<span data-ttu-id="42429-109">La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="42429-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="42429-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="42429-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="42429-111">Emplacement du cache à répertorier ou effacer.</span><span class="sxs-lookup"><span data-stu-id="42429-111">The cache location to list or clear.</span></span> <span data-ttu-id="42429-112">L’une des valeurs suivantes est acceptée :</span><span class="sxs-lookup"><span data-stu-id="42429-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="42429-113">`all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="42429-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="42429-114">`http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="42429-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="42429-115">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="42429-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="42429-116">`global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux.</span><span class="sxs-lookup"><span data-stu-id="42429-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="42429-117">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="42429-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="42429-118">`temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="42429-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="42429-119">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="42429-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="42429-120">Options</span><span class="sxs-lookup"><span data-stu-id="42429-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="42429-121">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="42429-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="42429-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="42429-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="42429-123">L’option clear exécute une opération d’effacement sur le type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="42429-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="42429-124">Le contenu des répertoires de cache est supprimé de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="42429-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="42429-125">Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache.</span><span class="sxs-lookup"><span data-stu-id="42429-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="42429-126">Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.</span><span class="sxs-lookup"><span data-stu-id="42429-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="42429-127">L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="42429-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="42429-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="42429-128">Examples</span></span>

- <span data-ttu-id="42429-129">Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="42429-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="42429-130">Affiche le chemin du répertoire du cache http local :</span><span class="sxs-lookup"><span data-stu-id="42429-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="42429-131">Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="42429-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="42429-132">Effacer tous les fichiers du répertoire du cache des packages globaux local :</span><span class="sxs-lookup"><span data-stu-id="42429-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="42429-133">Effacer tous les fichiers du répertoire du cache temporaire local :</span><span class="sxs-lookup"><span data-stu-id="42429-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="42429-134">Dépannage</span><span class="sxs-lookup"><span data-stu-id="42429-134">Troubleshooting</span></span>

<span data-ttu-id="42429-135">Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="42429-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
