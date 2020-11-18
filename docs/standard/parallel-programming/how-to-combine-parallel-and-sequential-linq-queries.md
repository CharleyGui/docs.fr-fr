---
title: 'Procédure : combiner des requêtes LINQ parallèles et séquentielles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: e851c6d72a5fd932c065368b893b907d7820c918
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827098"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Procédure : combiner des requêtes LINQ parallèles et séquentielles

Cet exemple montre comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.AsSequential%2A> pour indiquer à PLINQ de traiter de manière séquentielle tous les opérateurs suivants dans la requête. Bien que le traitement séquentiel soit souvent plus lent que parallèle, il est parfois nécessaire de produire des résultats corrects.  
  
> [!NOTE]
> Cet exemple est destiné à illustrer l’utilisation et peut ne pas s’exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un scénario dans lequel <xref:System.Linq.ParallelEnumerable.AsSequential%2A> est obligatoire, pour conserver le classement qui a été établi dans une clause précédente de la requête.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler et exécuter ce code, collez-le dans le projet d' [exemple de données PLINQ](plinq-data-sample.md) , ajoutez une ligne pour appeler la méthode à partir de `Main` et appuyez sur **F5**.  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
