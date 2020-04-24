---
title: Limitations de Xamarin
ms.date: 12/13/2019
description: Décrit certaines des limitations que vous pouvez rencontrer lors de l’utilisation de Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447166"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="ecaa1-103">Limitations de Xamarin</span><span class="sxs-lookup"><span data-stu-id="ecaa1-103">Xamarin limitations</span></span>

<span data-ttu-id="ecaa1-104">Les cibles Microsoft. Data. sqlite .NET Standard 2,0 et sont prises en charge sur Xamarin.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="ecaa1-105">Le tableau suivant indique les plateformes pour lesquelles le bundle SQLitePCLRaw par défaut fournit des binaires SQLite natifs.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="ecaa1-106">Pour plus d’informations sur l’utilisation d’un bundle différent ou la fourniture de vos propres binaires SQLite natifs, consultez [versions SQLite personnalisées](custom-versions.md) .</span><span class="sxs-lookup"><span data-stu-id="ecaa1-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="ecaa1-107">Plateforme</span><span class="sxs-lookup"><span data-stu-id="ecaa1-107">Platform</span></span> | <span data-ttu-id="ecaa1-108">Fichiers binaires SQLite</span><span class="sxs-lookup"><span data-stu-id="ecaa1-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="ecaa1-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="ecaa1-109">**Xamarin.Android**</span></span> | <span data-ttu-id="ecaa1-110">—</span><span class="sxs-lookup"><span data-stu-id="ecaa1-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="ecaa1-111">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="ecaa1-112">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="ecaa1-113">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="ecaa1-114">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-114">✔</span></span> |
| <span data-ttu-id="ecaa1-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="ecaa1-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="ecaa1-116">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-116">✔</span></span> |
| <span data-ttu-id="ecaa1-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="ecaa1-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="ecaa1-118">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-118">✔</span></span> |
| <span data-ttu-id="ecaa1-119">**Xamarin. TVOS**</span><span class="sxs-lookup"><span data-stu-id="ecaa1-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="ecaa1-120">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-120">✔</span></span> |
| <span data-ttu-id="ecaa1-121">**UWP**</span><span class="sxs-lookup"><span data-stu-id="ecaa1-121">**UWP**</span></span> | <span data-ttu-id="ecaa1-122">—</span><span class="sxs-lookup"><span data-stu-id="ecaa1-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="ecaa1-123">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="ecaa1-124">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="ecaa1-125">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="ecaa1-126">✔</span><span class="sxs-lookup"><span data-stu-id="ecaa1-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="ecaa1-127">iOS</span><span class="sxs-lookup"><span data-stu-id="ecaa1-127">iOS</span></span>

<span data-ttu-id="ecaa1-128">Microsoft. Data. sqlite tente d’initialiser automatiquement les bottes SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="ecaa1-129">Malheureusement, en raison des limitations de la compilation de l’AOA (Xamarin. iOS) pour. iOS, la tentative échoue et vous recevez l’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="ecaa1-130">Vous devez appeler `SQLitePCL.raw.SetProvider()`.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="ecaa1-131">Si vous utilisez un package de Bundle, cette opération s’effectue en `SQLitePCL.Batteries.Init()`appelant.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="ecaa1-132">Pour initialiser le bundle, ajoutez la ligne de code suivante à votre application avant d’utiliser Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="ecaa1-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="ecaa1-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecaa1-133">See also</span></span>

* [<span data-ttu-id="ecaa1-134">Limitations Async</span><span class="sxs-lookup"><span data-stu-id="ecaa1-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="ecaa1-135">Versions SQLite personnalisées</span><span class="sxs-lookup"><span data-stu-id="ecaa1-135">Custom SQLite versions</span></span>](custom-versions.md)
