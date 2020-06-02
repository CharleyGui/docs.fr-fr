---
title: 'Procédure : combiner des requêtes LINQ parallèles et séquentielles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289536"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="2662e-102">Procédure : combiner des requêtes LINQ parallèles et séquentielles</span><span class="sxs-lookup"><span data-stu-id="2662e-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="2662e-103">Cet exemple montre comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.AsSequential%2A> pour indiquer à PLINQ de traiter de manière séquentielle tous les opérateurs suivants dans la requête.</span><span class="sxs-lookup"><span data-stu-id="2662e-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="2662e-104">Bien que le traitement séquentiel soit souvent plus lent que parallèle, il est parfois nécessaire de produire des résultats corrects.</span><span class="sxs-lookup"><span data-stu-id="2662e-104">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2662e-105">Cet exemple est destiné à illustrer l’utilisation et peut ne pas s’exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="2662e-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="2662e-106">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2662e-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2662e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2662e-107">Example</span></span>  
 <span data-ttu-id="2662e-108">L’exemple suivant montre un scénario dans lequel <xref:System.Linq.ParallelEnumerable.AsSequential%2A> est obligatoire, pour conserver le classement qui a été établi dans une clause précédente de la requête.</span><span class="sxs-lookup"><span data-stu-id="2662e-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2662e-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2662e-109">Compiling the Code</span></span>  
 <span data-ttu-id="2662e-110">Pour compiler et exécuter ce code, collez-le dans le projet d' [exemple de données PLINQ](plinq-data-sample.md) , ajoutez une ligne pour appeler la méthode à partir de `Main` et appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="2662e-110">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2662e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2662e-111">See also</span></span>

- [<span data-ttu-id="2662e-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2662e-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
