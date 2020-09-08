---
title: Limitations Async
ms.date: 09/04/2020
description: Explique les limitations des API Async et certaines alternatives que vous pouvez utiliser à la place.
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515993"
---
# <a name="async-limitations"></a><span data-ttu-id="7c0f3-103">Limitations Async</span><span class="sxs-lookup"><span data-stu-id="7c0f3-103">Async limitations</span></span>

<span data-ttu-id="7c0f3-104">SQLite ne prend pas en charge les e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="7c0f3-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="7c0f3-105">Les méthodes Async ADO.NET s’exécutent de façon synchrone dans Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="7c0f3-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="7c0f3-106">Évitez de les appeler.</span><span class="sxs-lookup"><span data-stu-id="7c0f3-106">Avoid calling them.</span></span>

<span data-ttu-id="7c0f3-107">Utilisez plutôt un [cache partagé](connection-strings.md#cache) et une [journalisation avec écriture anticipée](https://www.sqlite.org/wal.html) pour améliorer les performances et l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="7c0f3-107">Instead, use a [shared cache](connection-strings.md#cache) and [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="7c0f3-108">La journalisation en écriture anticipée est activée par défaut sur les bases de données créées à l’aide de [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="7c0f3-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
