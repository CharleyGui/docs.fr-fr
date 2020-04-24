---
title: Limitations Async
ms.date: 12/13/2019
description: Explique les limitations des API Async et certaines alternatives que vous pouvez utiliser à la place.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447082"
---
# <a name="async-limitations"></a><span data-ttu-id="4e8cf-103">Limitations Async</span><span class="sxs-lookup"><span data-stu-id="4e8cf-103">Async limitations</span></span>

<span data-ttu-id="4e8cf-104">SQLite ne prend pas en charge les e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="4e8cf-105">Les méthodes Async ADO.NET s’exécutent de façon synchrone dans Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="4e8cf-106">Évitez de les appeler.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-106">Avoid calling them.</span></span>

<span data-ttu-id="4e8cf-107">Utilisez plutôt la [journalisation avec écriture anticipée](https://www.sqlite.org/wal.html) pour améliorer les performances et l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="4e8cf-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="4e8cf-108">La journalisation en écriture anticipée est activée par défaut sur les bases de données créées à l’aide de [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="4e8cf-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
