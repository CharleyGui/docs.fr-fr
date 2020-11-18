---
title: 'Procédure : écrire une fonction d’agrégation PLINQ personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: d04f90e9c763c8ddba5ba07b650ffb878869ff3a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825466"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Procédure : écrire une fonction d’agrégation PLINQ personnalisée
Cet exemple montre comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pour appliquer une fonction d’agrégation personnalisée à une séquence source.  
  
> [!WARNING]
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant calcule l’écart type d’une séquence d’entiers.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Cet exemple utilise une surcharge de l’opérateur de requête standard d’agrégation propre à PLINQ. Cette surcharge accepte un <xref:System.Func%603?displayProperty=nameWithType> supplémentaire en tant que troisième paramètre d’entrée. Ce délégué combine les résultats de tous les threads avant d’effectuer le calcul final à partir des résultats agrégés. Dans cet exemple, nous regroupons les sommes de tous les threads.  
  
 Notez que quand un corps d’expression lambda se compose d’une expression unique, la valeur de retour du délégué <xref:System.Func%602?displayProperty=nameWithType> correspond à la valeur de l’expression.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
