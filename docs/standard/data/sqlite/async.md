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
# <a name="async-limitations"></a>Limitations Async

SQLite ne prend pas en charge les e/s asynchrones. Les méthodes Async ADO.NET s’exécutent de façon synchrone dans Microsoft. Data. sqlite. Évitez de les appeler.

Utilisez plutôt la [journalisation avec écriture anticipée](https://www.sqlite.org/wal.html) pour améliorer les performances et l’accès concurrentiel.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> La journalisation en écriture anticipée est activée par défaut sur les bases de données créées à l’aide de [Entity Framework Core](/ef/core/).
