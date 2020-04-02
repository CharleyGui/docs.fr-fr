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
ms.openlocfilehash: 6ef813937b731b417be31e189d89b81cccc75280
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588548"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="caac8-102">Comment : spécifier le mode d'exécution en PLINQ</span><span class="sxs-lookup"><span data-stu-id="caac8-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="caac8-103">Cet exemple montre comment forcer PLINQ à contourner ses paramètres heuristiques et à paralléliser une requête quelle que soit sa forme.</span><span class="sxs-lookup"><span data-stu-id="caac8-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="caac8-104">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="caac8-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="caac8-105">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="caac8-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="caac8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="caac8-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="caac8-107">PLINQ est conçu pour exploiter les opportunités de parallélisation.</span><span class="sxs-lookup"><span data-stu-id="caac8-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="caac8-108">Toutefois, toutes les requêtes ne bénéficient pas de l’exécution parallèle.</span><span class="sxs-lookup"><span data-stu-id="caac8-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="caac8-109">Par exemple, lorsqu’une requête contient un délégué d’utilisateur unique qui travaille très peu, elle est généralement exécutée plus rapidement de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="caac8-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="caac8-110">Ceci est dû au fait que la surcharge impliquée dans l’activation de l’exécution de parallélisatione est plus coûteuse que l’accélération obtenue.</span><span class="sxs-lookup"><span data-stu-id="caac8-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="caac8-111">Par conséquent, PLINQ ne pas parallélise pas automatiquement chaque requête.</span><span class="sxs-lookup"><span data-stu-id="caac8-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="caac8-112">Il examine d’abord la forme de la requête et les différents opérateurs qui la composent.</span><span class="sxs-lookup"><span data-stu-id="caac8-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="caac8-113">En fonction de cette analyse, en mode d’exécution par défaut PLINQ peut décider d’exécuter de manière séquentielle une partie de la requête ou sa totalité.</span><span class="sxs-lookup"><span data-stu-id="caac8-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="caac8-114">Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n’est en mesure de déterminer à partir de son analyse.</span><span class="sxs-lookup"><span data-stu-id="caac8-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="caac8-115">Par exemple, vous pouvez savoir qu’un délégué est très coûteux et que la requête bénéficiera assurément de la parallélisation.</span><span class="sxs-lookup"><span data-stu-id="caac8-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="caac8-116">Dans ce cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode.ForceParallelism> pour indiquer à PLINQ de toujours exécuter la requête en parallèle.</span><span class="sxs-lookup"><span data-stu-id="caac8-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="caac8-117">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="caac8-117">Compiling the Code</span></span>  
 <span data-ttu-id="caac8-118">Coupez et collez ce code dans l’[échantillon de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appelez la méthode à partir de `Main`.</span><span class="sxs-lookup"><span data-stu-id="caac8-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caac8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caac8-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="caac8-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="caac8-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
