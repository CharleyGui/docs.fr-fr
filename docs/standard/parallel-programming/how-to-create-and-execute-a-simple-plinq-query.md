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
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635852"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="c453f-102">Comment : créer et exécuter une requête PLINQ simple</span><span class="sxs-lookup"><span data-stu-id="c453f-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="c453f-103">L’exemple de cet article montre comment créer une simple requête en langage <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> parallèle intégrée (LINQ) en utilisant la <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> méthode d’extension sur la séquence source et en exécutant la requête en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="c453f-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c453f-104">Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c453f-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c453f-105">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c453f-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c453f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c453f-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="c453f-107">Cet exemple démontre le modèle de base pour créer et exécuter toute requête parallèle LINQ lorsque la commande de la séquence de résultat n’est pas importante.</span><span class="sxs-lookup"><span data-stu-id="c453f-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="c453f-108">Les requêtes non ordonnées sont généralement plus rapides que les requêtes commandées.</span><span class="sxs-lookup"><span data-stu-id="c453f-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="c453f-109">La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="c453f-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="c453f-110">L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread.</span><span class="sxs-lookup"><span data-stu-id="c453f-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="c453f-111">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="c453f-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c453f-112">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c453f-112">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="c453f-113">Pour plus d'informations sur la conservation du classement des éléments d'une requête, consultez [Comment : contrôler l'ordre dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c453f-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c453f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c453f-114">See also</span></span>

- [<span data-ttu-id="c453f-115">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c453f-115">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
