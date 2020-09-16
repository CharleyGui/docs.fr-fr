---
title: 'Procédure : créer et exécuter une requête PLINQ simple'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: a5f6a26ada321bd351249c5179d050ee571b550c
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679335"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Procédure : créer et exécuter une requête PLINQ simple

L’exemple de cet article montre comment créer une requête LINQ (Parallel Language Integrated Query) simple en utilisant la <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> méthode d’extension sur la séquence source et en exécutant la requête à l’aide de la <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> méthode.  
  
> [!NOTE]
> Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ. Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a> Exemple  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Cet exemple illustre le modèle de base pour la création et l’exécution de toute requête Parallel LINQ lorsque l’ordre de la séquence de résultat n’est pas important. Les requêtes non ordonnées sont généralement plus rapides que les requêtes classées. La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads. L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread. Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md). Pour plus d'informations sur la conservation du classement des éléments d'une requête, consultez [Comment : contrôler l'ordre dans une requête PLINQ](how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
