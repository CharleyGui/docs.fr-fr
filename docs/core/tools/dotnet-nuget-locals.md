---
title: Commande dotnet nuget locals
description: La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 0a9fd7876aa4d1907eb37e6bac54295d938d36d3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632425"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="58cd1-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="58cd1-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="58cd1-104">Name</span><span class="sxs-lookup"><span data-stu-id="58cd1-104">Name</span></span>

<span data-ttu-id="58cd1-105">`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.</span><span class="sxs-lookup"><span data-stu-id="58cd1-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="58cd1-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="58cd1-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="58cd1-107">Description</span><span class="sxs-lookup"><span data-stu-id="58cd1-107">Description</span></span>

<span data-ttu-id="58cd1-108">La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="58cd1-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="58cd1-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="58cd1-109">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="58cd1-110">Emplacement du cache à répertorier ou effacer.</span><span class="sxs-lookup"><span data-stu-id="58cd1-110">The cache location to list or clear.</span></span> <span data-ttu-id="58cd1-111">L’une des valeurs suivantes est acceptée :</span><span class="sxs-lookup"><span data-stu-id="58cd1-111">It accepts one of the following values:</span></span>

  * <span data-ttu-id="58cd1-112">`all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="58cd1-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="58cd1-113">`http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="58cd1-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="58cd1-114">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="58cd1-114">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="58cd1-115">`global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux.</span><span class="sxs-lookup"><span data-stu-id="58cd1-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="58cd1-116">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="58cd1-116">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="58cd1-117">`temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="58cd1-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="58cd1-118">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="58cd1-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="58cd1-119">Options</span><span class="sxs-lookup"><span data-stu-id="58cd1-119">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="58cd1-120">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="58cd1-120">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="58cd1-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="58cd1-121">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="58cd1-122">L’option clear exécute une opération d’effacement sur le type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="58cd1-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="58cd1-123">Le contenu des répertoires de cache est supprimé de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="58cd1-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="58cd1-124">Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache.</span><span class="sxs-lookup"><span data-stu-id="58cd1-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="58cd1-125">Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.</span><span class="sxs-lookup"><span data-stu-id="58cd1-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="58cd1-126">L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="58cd1-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="58cd1-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="58cd1-127">Examples</span></span>

* <span data-ttu-id="58cd1-128">Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="58cd1-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="58cd1-129">Affiche le chemin du répertoire du cache http local :</span><span class="sxs-lookup"><span data-stu-id="58cd1-129">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="58cd1-130">Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="58cd1-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="58cd1-131">Effacer tous les fichiers du répertoire du cache des packages globaux local :</span><span class="sxs-lookup"><span data-stu-id="58cd1-131">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="58cd1-132">Effacer tous les fichiers du répertoire du cache temporaire local :</span><span class="sxs-lookup"><span data-stu-id="58cd1-132">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="58cd1-133">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="58cd1-133">Troubleshooting</span></span>

<span data-ttu-id="58cd1-134">Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="58cd1-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
