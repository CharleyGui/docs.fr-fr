---
title: 'Comment : créer et exécuter une requête PLINQ simple'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 0cdef6d3826e4e7522bf3f6ed69060b8ef1c5e1b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588295"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Comment : créer et exécuter une requête PLINQ simple
L’exemple suivant montre comment créer une requête Parallel LINQ simple à l’aide de la méthode d’extension <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sur la séquence source, et exécuter la requête à l’aide de la méthode <xref:System.Linq.ParallelEnumerable.ForAll%2A>.  
  
> [!NOTE]
> Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ. Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Cet exemple montre le modèle de base pour la création et l’exécution d’une requête Parallel LINQ quand le classement de la séquence de résultat n’est pas important ; les requêtes non classées sont généralement plus rapides que les requêtes classées. La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads. L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread. Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Pour plus d'informations sur la conservation du classement des éléments d'une requête, consultez [Comment : contrôler l'ordre dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
