---
title: 'Comment : mesurer les performances de requêtes PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 37bd3bc464f719876b2fe13ee1a11ebca4339988
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635832"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="ee21f-102">Comment : mesurer les performances de requêtes PLINQ</span><span class="sxs-lookup"><span data-stu-id="ee21f-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="ee21f-103">Cet exemple montre comment <xref:System.Diagnostics.Stopwatch> utiliser la classe pour mesurer le temps qu’il faut pour qu’une requête PLINQ s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ee21f-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee21f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee21f-104">Example</span></span>  
 <span data-ttu-id="ee21f-105">Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="ee21f-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="ee21f-106">Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête.</span><span class="sxs-lookup"><span data-stu-id="ee21f-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="ee21f-107">Notez que le chronomètre n’est pas commencé jusqu’à ce que juste avant la boucle, parce que c’est là que l’exécution de la requête commence.</span><span class="sxs-lookup"><span data-stu-id="ee21f-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="ee21f-108">Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="ee21f-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="ee21f-109">Le temps d’exécution total est une mesure utile lorsque vous expérimentez avec des implémentations de requêtes, mais il ne dit pas toujours toute l’histoire.</span><span class="sxs-lookup"><span data-stu-id="ee21f-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="ee21f-110">Pour obtenir une vue plus profonde et plus riche de l’interaction des fils de requête les uns avec les autres et avec d’autres processus en cours d’exécution, utilisez le [Visualizer Concurrency](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="ee21f-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee21f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee21f-111">See also</span></span>

- [<span data-ttu-id="ee21f-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ee21f-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
