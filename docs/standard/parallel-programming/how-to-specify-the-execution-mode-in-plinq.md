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
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635808"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Comment : spécifier le mode d'exécution en PLINQ

Cet exemple montre comment forcer PLINQ à contourner ses paramètres heuristiques et à paralléliser une requête quelle que soit sa forme.  
  
> [!NOTE]
> Cet exemple est destiné à démontrer l’utilisation et pourrait ne pas courir plus vite que l’équivalent Séquentiel LINQ à la requête Objets. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ est conçu pour exploiter les opportunités de parallélisation. Toutefois, toutes les requêtes ne bénéficient pas de l’exécution parallèle. Par exemple, lorsqu’une requête contient un seul délégué utilisateur qui fait peu de travail, la requête s’exécute généralement plus rapidement en séquentiel. L’exécution séquentielle est plus rapide parce que les frais généraux impliqués dans l’exécution de parallélisation sont plus chers que le speedup qui est obtenu. Par conséquent, PLINQ ne pas parallélise pas automatiquement chaque requête. Il examine d’abord la forme de la requête et les différents opérateurs qui la composent. En fonction de cette analyse, en mode d’exécution par défaut PLINQ peut décider d’exécuter de manière séquentielle une partie de la requête ou sa totalité. Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n’est en mesure de déterminer à partir de son analyse. Par exemple, vous savez peut-être qu’un délégué coûte cher et que la requête bénéficiera certainement d’une parallélisation. Dans ce cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode.ForceParallelism> pour indiquer à PLINQ de toujours exécuter la requête en parallèle.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Coupez et collez ce code dans l’[échantillon de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appelez la méthode à partir de `Main`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
