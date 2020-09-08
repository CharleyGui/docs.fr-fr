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
# <a name="async-limitations"></a>Limitations Async

SQLite ne prend pas en charge les e/s asynchrones. Les méthodes Async ADO.NET s’exécutent de façon synchrone dans Microsoft. Data. sqlite. Évitez de les appeler.

Utilisez plutôt un [cache partagé](connection-strings.md#cache) et une [journalisation avec écriture anticipée](https://www.sqlite.org/wal.html) pour améliorer les performances et l’accès concurrentiel.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> La journalisation en écriture anticipée est activée par défaut sur les bases de données créées à l’aide de [Entity Framework Core](/ef/core/).
