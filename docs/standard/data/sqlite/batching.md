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
# <a name="batching"></a><span data-ttu-id="e77fb-103">Traitement par lots</span><span class="sxs-lookup"><span data-stu-id="e77fb-103">Batching</span></span>

<span data-ttu-id="e77fb-104">SQLite ne prend pas en charge en mode natif le traitement par lot des instructions SQL dans une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e77fb-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="e77fb-105">Toutefois, étant donné qu’il n’y a pas de réseau impliqué, cela ne permet pas vraiment d’améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="e77fb-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="e77fb-106">Toutefois, Microsoft. Data. sqlite implémente le traitement par lots d’instructions pour faire en sorte qu’il se comporte davantage comme les autres fournisseurs ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e77fb-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="e77fb-107">Lors de l’appel de <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, les instructions sont exécutées jusqu’au premier qui retourne les résultats.</span><span class="sxs-lookup"><span data-stu-id="e77fb-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="e77fb-108">L’appel de <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> poursuit l’exécution des instructions jusqu’au prochain qui retourne les résultats ou jusqu’à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="e77fb-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="e77fb-109">L’appel de <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> ou <xref:System.Data.Common.DbDataReader.Close%2A> exécute toutes les instructions restantes qui n’ont pas été consommées par `NextResult()`.</span><span class="sxs-lookup"><span data-stu-id="e77fb-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="e77fb-110">Si vous ne supprimez pas un lecteur de données, le finaliseur tente d’exécuter les instructions restantes, mais toutes les erreurs qu’il rencontre sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="e77fb-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="e77fb-111">Pour cette raison, il est important de supprimer les objets `DbDataReader` lors de l’utilisation de lots.</span><span class="sxs-lookup"><span data-stu-id="e77fb-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="e77fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e77fb-112">See also</span></span>

* [<span data-ttu-id="e77fb-113">Insertion en bloc</span><span class="sxs-lookup"><span data-stu-id="e77fb-113">Bulk Insert</span></span>](bulk-insert.md)
