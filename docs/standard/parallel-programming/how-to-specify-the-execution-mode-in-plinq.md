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
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635808"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="aa64d-102">Comment : spécifier le mode d'exécution en PLINQ</span><span class="sxs-lookup"><span data-stu-id="aa64d-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="aa64d-103">Cet exemple montre comment forcer PLINQ à contourner ses paramètres heuristiques et à paralléliser une requête quelle que soit sa forme.</span><span class="sxs-lookup"><span data-stu-id="aa64d-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa64d-104">Cet exemple est destiné à démontrer l’utilisation et pourrait ne pas courir plus vite que l’équivalent Séquentiel LINQ à la requête Objets.</span><span class="sxs-lookup"><span data-stu-id="aa64d-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="aa64d-105">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="aa64d-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa64d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa64d-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="aa64d-107">PLINQ est conçu pour exploiter les opportunités de parallélisation.</span><span class="sxs-lookup"><span data-stu-id="aa64d-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="aa64d-108">Toutefois, toutes les requêtes ne bénéficient pas de l’exécution parallèle.</span><span class="sxs-lookup"><span data-stu-id="aa64d-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="aa64d-109">Par exemple, lorsqu’une requête contient un seul délégué utilisateur qui fait peu de travail, la requête s’exécute généralement plus rapidement en séquentiel.</span><span class="sxs-lookup"><span data-stu-id="aa64d-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="aa64d-110">L’exécution séquentielle est plus rapide parce que les frais généraux impliqués dans l’exécution de parallélisation sont plus chers que le speedup qui est obtenu.</span><span class="sxs-lookup"><span data-stu-id="aa64d-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="aa64d-111">Par conséquent, PLINQ ne pas parallélise pas automatiquement chaque requête.</span><span class="sxs-lookup"><span data-stu-id="aa64d-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="aa64d-112">Il examine d’abord la forme de la requête et les différents opérateurs qui la composent.</span><span class="sxs-lookup"><span data-stu-id="aa64d-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="aa64d-113">En fonction de cette analyse, en mode d’exécution par défaut PLINQ peut décider d’exécuter de manière séquentielle une partie de la requête ou sa totalité.</span><span class="sxs-lookup"><span data-stu-id="aa64d-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="aa64d-114">Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n’est en mesure de déterminer à partir de son analyse.</span><span class="sxs-lookup"><span data-stu-id="aa64d-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="aa64d-115">Par exemple, vous savez peut-être qu’un délégué coûte cher et que la requête bénéficiera certainement d’une parallélisation.</span><span class="sxs-lookup"><span data-stu-id="aa64d-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="aa64d-116">Dans ce cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode.ForceParallelism> pour indiquer à PLINQ de toujours exécuter la requête en parallèle.</span><span class="sxs-lookup"><span data-stu-id="aa64d-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa64d-117">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="aa64d-117">Compiling the Code</span></span>  
 <span data-ttu-id="aa64d-118">Coupez et collez ce code dans l’[échantillon de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appelez la méthode à partir de `Main`.</span><span class="sxs-lookup"><span data-stu-id="aa64d-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa64d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa64d-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="aa64d-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="aa64d-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
