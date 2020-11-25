---
title: 'Procédure : spécifier des options de fusion avec PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 7c7979dc828f89435422b464b22710b3a052911b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722425"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Procédure : spécifier des options de fusion avec PLINQ

Cet exemple montre comment spécifier les options de fusion qui seront appliquées à tous les opérateurs suivants dans une requête PLINQ. Il n’est pas nécessaire de définir explicitement les options de fusion, mais cela peut améliorer les performances. Pour plus d’informations sur les options de fusion, consultez [Options de fusion en PLINQ](merge-options-in-plinq.md).  
  
> [!WARNING]
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre le comportement des options de fusion dans un scénario de base qui a une source non ordonnée et qui applique une fonction coûteuse à chaque élément.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Dans les cas où l’option <xref:System.Linq.ParallelMergeOptions.AutoBuffered> entraînerait une latence indésirable avant la transmission du premier élément, essayez l’option <xref:System.Linq.ParallelMergeOptions.NotBuffered> pour transmettre des éléments de résultat plus rapidement et plus facilement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelMergeOptions>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
