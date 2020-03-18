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
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124991"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="83d7f-102">Comment : mesurer les performances de requêtes PLINQ</span><span class="sxs-lookup"><span data-stu-id="83d7f-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="83d7f-103">Cet exemple montre comment utiliser la classe <xref:System.Diagnostics.Stopwatch> pour mesurer le temps nécessaire à l’exécution d’une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="83d7f-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83d7f-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="83d7f-104">Example</span></span>  
 <span data-ttu-id="83d7f-105">Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="83d7f-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="83d7f-106">Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête.</span><span class="sxs-lookup"><span data-stu-id="83d7f-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="83d7f-107">Notez que le chronomètre est démarré juste avant la boucle qui marque le début d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="83d7f-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="83d7f-108">Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="83d7f-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="83d7f-109">La durée d’exécution totale est une mesure utile lorsque vous expérimentez des implémentations de requête, même si elle ne donne pas toujours tous les détails.</span><span class="sxs-lookup"><span data-stu-id="83d7f-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="83d7f-110">Utilisez le visualiseur concurrentiel pour avoir une vision plus approfondie et plus riche de l’interaction des threads de requête entre eux et avec d’autres processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="83d7f-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="83d7f-111">Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="83d7f-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d7f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d7f-112">See also</span></span>

- [<span data-ttu-id="83d7f-113">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="83d7f-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
