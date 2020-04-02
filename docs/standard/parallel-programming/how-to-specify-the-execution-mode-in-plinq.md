---
title: "Comment : spécifier le mode d'exécution en PLINQ"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 6ef813937b731b417be31e189d89b81cccc75280
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588548"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Comment : spécifier le mode d'exécution en PLINQ
Cet exemple montre comment forcer PLINQ à contourner ses paramètres heuristiques et à paralléliser une requête quelle que soit sa forme.  
  
> [!WARNING]
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ est conçu pour exploiter les opportunités de parallélisation. Toutefois, toutes les requêtes ne bénéficient pas de l’exécution parallèle. Par exemple, lorsqu’une requête contient un délégué d’utilisateur unique qui travaille très peu, elle est généralement exécutée plus rapidement de manière séquentielle. Ceci est dû au fait que la surcharge impliquée dans l’activation de l’exécution de parallélisatione est plus coûteuse que l’accélération obtenue. Par conséquent, PLINQ ne pas parallélise pas automatiquement chaque requête. Il examine d’abord la forme de la requête et les différents opérateurs qui la composent. En fonction de cette analyse, en mode d’exécution par défaut PLINQ peut décider d’exécuter de manière séquentielle une partie de la requête ou sa totalité. Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n’est en mesure de déterminer à partir de son analyse. Par exemple, vous pouvez savoir qu’un délégué est très coûteux et que la requête bénéficiera assurément de la parallélisation. Dans ce cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode.ForceParallelism> pour indiquer à PLINQ de toujours exécuter la requête en parallèle.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Coupez et collez ce code dans l’[échantillon de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appelez la méthode à partir de `Main`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
