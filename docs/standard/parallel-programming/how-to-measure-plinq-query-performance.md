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
# <a name="how-to-measure-plinq-query-performance"></a>Comment : mesurer les performances de requêtes PLINQ

Cet exemple montre comment <xref:System.Diagnostics.Stopwatch> utiliser la classe pour mesurer le temps qu’il faut pour qu’une requête PLINQ s’exécute.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête. Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête. Notez que le chronomètre n’est pas commencé jusqu’à ce que juste avant la boucle, parce que c’est là que l’exécution de la requête commence. Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Le temps d’exécution total est une mesure utile lorsque vous expérimentez avec des implémentations de requêtes, mais il ne dit pas toujours toute l’histoire. Pour obtenir une vue plus profonde et plus riche de l’interaction des fils de requête les uns avec les autres et avec d’autres processus en cours d’exécution, utilisez le [Visualizer Concurrency](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
