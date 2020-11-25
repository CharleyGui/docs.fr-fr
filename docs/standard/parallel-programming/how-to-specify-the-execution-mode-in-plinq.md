---
title: 'Procédure : spécifier le mode d’exécution avec PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 725f232337952449cd8569b12f65da75569996df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722390"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Procédure : spécifier le mode d’exécution avec PLINQ

Cet exemple montre comment forcer PLINQ à contourner ses paramètres heuristiques et à paralléliser une requête quelle que soit sa forme.  
  
> [!NOTE]
> Cet exemple est destiné à illustrer l’utilisation et peut ne pas s’exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ est conçu pour exploiter les opportunités de parallélisation. Toutefois, toutes les requêtes ne bénéficient pas de l’exécution parallèle. Par exemple, lorsqu’une requête contient un délégué d’utilisateur unique qui ne fonctionne que peu, la requête s’exécute généralement plus rapidement. L’exécution séquentielle est plus rapide, car la surcharge impliquée dans l’activation de la parallélisation d’exécution est plus coûteuse que l’accélération obtenue. Par conséquent, PLINQ ne pas parallélise pas automatiquement chaque requête. Il examine d’abord la forme de la requête et les différents opérateurs qui la composent. En fonction de cette analyse, en mode d’exécution par défaut PLINQ peut décider d’exécuter de manière séquentielle une partie de la requête ou sa totalité. Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n’est en mesure de déterminer à partir de son analyse. Par exemple, vous savez peut-être qu’un délégué est onéreux et que la requête bénéficiera de la parallélisation. Dans ce cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode.ForceParallelism> pour indiquer à PLINQ de toujours exécuter la requête en parallèle.  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Coupez et collez ce code dans l’[échantillon de données PLINQ](plinq-data-sample.md) et appelez la méthode à partir de `Main`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
