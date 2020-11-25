---
title: 'Procédure : mesurer les performances de requêtes PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 2cbd178d5004d28120ab701a777a474a7e78e09e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734437"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="2d931-102">Procédure : mesurer les performances de requêtes PLINQ</span><span class="sxs-lookup"><span data-stu-id="2d931-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="2d931-103">Cet exemple montre comment utiliser la <xref:System.Diagnostics.Stopwatch> classe pour mesurer le temps nécessaire à l’exécution d’une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2d931-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d931-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d931-104">Example</span></span>  

 <span data-ttu-id="2d931-105">Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="2d931-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="2d931-106">Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête.</span><span class="sxs-lookup"><span data-stu-id="2d931-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="2d931-107">Notez que le chronomètre n’est pas démarré avant la boucle, car c’est à ce moment-là que l’exécution de la requête commence.</span><span class="sxs-lookup"><span data-stu-id="2d931-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="2d931-108">Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="2d931-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="2d931-109">La durée totale d’exécution est une mesure utile lorsque vous expérimentez des implémentations de requêtes, mais n’indique pas toujours l’histoire entière.</span><span class="sxs-lookup"><span data-stu-id="2d931-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="2d931-110">Pour obtenir une vue plus détaillée et plus riche de l’interaction des threads de requête les uns avec les autres et avec d’autres processus en cours d’exécution, utilisez le [visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="2d931-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d931-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d931-111">See also</span></span>

- [<span data-ttu-id="2d931-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2d931-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
