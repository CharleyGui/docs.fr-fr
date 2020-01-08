---
title: Traitement par lots
ms.date: 12/13/2019
description: Découvrez comment exécuter un lot d’instructions SQL dans une seule commande.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447054"
---
# <a name="batching"></a>Traitement par lots

SQLite ne prend pas en charge en mode natif le traitement par lot des instructions SQL dans une seule commande. Toutefois, étant donné qu’il n’y a pas de réseau impliqué, cela ne permet pas vraiment d’améliorer les performances. Toutefois, Microsoft. Data. sqlite implémente le traitement par lots d’instructions pour faire en sorte qu’il se comporte davantage comme les autres fournisseurs ADO.NET.

Lors de l’appel de <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, les instructions sont exécutées jusqu’au premier qui retourne les résultats. L’appel de <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> poursuit l’exécution des instructions jusqu’au prochain qui retourne les résultats ou jusqu’à la fin du traitement. L’appel de <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> ou <xref:System.Data.Common.DbDataReader.Close%2A> exécute toutes les instructions restantes qui n’ont pas été consommées par `NextResult()`. Si vous ne supprimez pas un lecteur de données, le finaliseur tente d’exécuter les instructions restantes, mais toutes les erreurs qu’il rencontre sont ignorées. Pour cette raison, il est important de supprimer les objets `DbDataReader` lors de l’utilisation de lots.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>Voir aussi

* [Insertion en bloc](bulk-insert.md)
