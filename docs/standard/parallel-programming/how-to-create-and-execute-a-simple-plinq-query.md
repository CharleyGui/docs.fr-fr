---
title: 'Procédure : créer et exécuter une requête PLINQ simple'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 228a94323c42d7c7a5ecbd295a0db5d73f4f1f49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703692"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="77e59-102">Procédure : créer et exécuter une requête PLINQ simple</span><span class="sxs-lookup"><span data-stu-id="77e59-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="77e59-103">L’exemple de cet article montre comment créer une requête LINQ (Parallel Language Integrated Query) simple en utilisant la <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> méthode d’extension sur la séquence source et en exécutant la requête à l’aide de la <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="77e59-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77e59-104">Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="77e59-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="77e59-105">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="77e59-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77e59-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="77e59-106">Example</span></span>  

 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="77e59-107">Cet exemple illustre le modèle de base pour la création et l’exécution de toute requête Parallel LINQ lorsque l’ordre de la séquence de résultat n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="77e59-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="77e59-108">Les requêtes non ordonnées sont généralement plus rapides que les requêtes classées.</span><span class="sxs-lookup"><span data-stu-id="77e59-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="77e59-109">La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="77e59-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="77e59-110">L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread.</span><span class="sxs-lookup"><span data-stu-id="77e59-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="77e59-111">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="77e59-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="77e59-112">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="77e59-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="77e59-113">Pour plus d'informations sur la conservation du classement des éléments d'une requête, consultez [Comment : contrôler l'ordre dans une requête PLINQ](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="77e59-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e59-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77e59-114">See also</span></span>

- [<span data-ttu-id="77e59-115">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="77e59-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
