---
title: Commande dotnet nuget delete
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733124"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="6f8a7-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="6f8a7-103">dotnet nuget delete</span></span>

<span data-ttu-id="6f8a7-104">**Cet article s’applique à:** ✔️ .NET Core 1.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6f8a7-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="6f8a7-105">Nom</span><span class="sxs-lookup"><span data-stu-id="6f8a7-105">Name</span></span>

<span data-ttu-id="6f8a7-106">`dotnet nuget delete` -Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6f8a7-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6f8a7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="6f8a7-108">Description</span><span class="sxs-lookup"><span data-stu-id="6f8a7-108">Description</span></span>

<span data-ttu-id="6f8a7-109">La commande `dotnet nuget delete` supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="6f8a7-110">Pour [nuget.org,](https://www.nuget.org/)l’action consiste à délister le paquet.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="6f8a7-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="6f8a7-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="6f8a7-112">Nom/ID du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="6f8a7-113">Version du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="6f8a7-114">Options</span><span class="sxs-lookup"><span data-stu-id="6f8a7-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="6f8a7-115">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="6f8a7-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="6f8a7-116">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="6f8a7-117">Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="6f8a7-118">Option disponible à partir du SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="6f8a7-119">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="6f8a7-120">N’ajoute pas « api/v2/package » à l’URL source.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="6f8a7-121">Option disponible à partir du kit SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="6f8a7-122">Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="6f8a7-123">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-123">Specifies the server URL.</span></span> <span data-ttu-id="6f8a7-124">Les URL prises en charge pour nuget.org incluent `https://www.nuget.org`, `https://www.nuget.org/api/v3` et `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="6f8a7-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="6f8a7-125">Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="6f8a7-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="6f8a7-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="6f8a7-126">Examples</span></span>

* <span data-ttu-id="6f8a7-127">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :</span><span class="sxs-lookup"><span data-stu-id="6f8a7-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="6f8a7-128">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :</span><span class="sxs-lookup"><span data-stu-id="6f8a7-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
