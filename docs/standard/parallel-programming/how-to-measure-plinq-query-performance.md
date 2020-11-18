---
title: 'Procédure : mesurer les performances de requêtes PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 43f83a34531b853d108785052f637d9568c45280
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826877"
---
# <a name="how-to-measure-plinq-query-performance"></a>Procédure : mesurer les performances de requêtes PLINQ

Cet exemple montre comment utiliser la <xref:System.Diagnostics.Stopwatch> classe pour mesurer le temps nécessaire à l’exécution d’une requête PLINQ.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête. Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête. Notez que le chronomètre n’est pas démarré avant la boucle, car c’est à ce moment-là que l’exécution de la requête commence. Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 La durée totale d’exécution est une mesure utile lorsque vous expérimentez des implémentations de requêtes, mais n’indique pas toujours l’histoire entière. Pour obtenir une vue plus détaillée et plus riche de l’interaction des threads de requête les uns avec les autres et avec d’autres processus en cours d’exécution, utilisez le [visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
