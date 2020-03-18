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
ms.openlocfilehash: 349cc8d78e9a080d720e09a7e3e5e314752605c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106957"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="92a79-102">Comment : créer et exécuter une requête PLINQ simple</span><span class="sxs-lookup"><span data-stu-id="92a79-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="92a79-103">L’exemple suivant montre comment créer une requête Parallel LINQ simple à l’aide de la méthode d’extension <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sur la séquence source, et exécuter la requête à l’aide de la méthode <xref:System.Linq.ParallelEnumerable.ForAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a79-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92a79-104">Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="92a79-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="92a79-105">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="92a79-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92a79-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="92a79-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="92a79-107">Cet exemple montre le modèle de base pour la création et l’exécution d’une requête Parallel LINQ quand le classement de la séquence de résultat n’est pas important ; les requêtes non classées sont généralement plus rapides que les requêtes classées.</span><span class="sxs-lookup"><span data-stu-id="92a79-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="92a79-108">La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="92a79-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="92a79-109">L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread.</span><span class="sxs-lookup"><span data-stu-id="92a79-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="92a79-110">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="92a79-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="92a79-111">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="92a79-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="92a79-112">Pour plus d'informations sur la conservation du classement des éléments d'une requête, consultez [Comment : contrôler l'ordre dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="92a79-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a79-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92a79-113">See also</span></span>

- [<span data-ttu-id="92a79-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="92a79-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
