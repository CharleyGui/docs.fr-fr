---
title: Commande dotnet nuget delete
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 70316a0baa2cf9923738a53af561b5c77014c3ff
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202570"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="95742-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="95742-103">dotnet nuget delete</span></span>

<span data-ttu-id="95742-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="95742-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="95742-105">Name</span><span class="sxs-lookup"><span data-stu-id="95742-105">Name</span></span>

<span data-ttu-id="95742-106">`dotnet nuget delete` -Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="95742-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="95742-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="95742-107">Synopsis</span></span>

```console
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="95742-108">Description</span><span class="sxs-lookup"><span data-stu-id="95742-108">Description</span></span>

<span data-ttu-id="95742-109">La commande `dotnet nuget delete` supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="95742-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="95742-110">Pour [nuget.org](https://www.nuget.org/), l’action consiste à supprimer le package de la liste.</span><span class="sxs-lookup"><span data-stu-id="95742-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="95742-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="95742-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="95742-112">Nom/ID du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="95742-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="95742-113">Version du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="95742-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="95742-114">Options</span><span class="sxs-lookup"><span data-stu-id="95742-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="95742-115">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="95742-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="95742-116">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="95742-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="95742-117">Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification.</span><span class="sxs-lookup"><span data-stu-id="95742-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="95742-118">Option disponible à partir du SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="95742-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="95742-119">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="95742-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="95742-120">N’ajoute pas « api/v2/package » à l’URL source.</span><span class="sxs-lookup"><span data-stu-id="95742-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="95742-121">Option disponible à partir du kit SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="95742-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="95742-122">Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95742-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="95742-123">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="95742-123">Specifies the server URL.</span></span> <span data-ttu-id="95742-124">Les URL prises en charge pour nuget.org incluent `https://www.nuget.org`, `https://www.nuget.org/api/v3` et `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="95742-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="95742-125">Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="95742-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="95742-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="95742-126">Examples</span></span>

* <span data-ttu-id="95742-127">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :</span><span class="sxs-lookup"><span data-stu-id="95742-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="95742-128">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :</span><span class="sxs-lookup"><span data-stu-id="95742-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
