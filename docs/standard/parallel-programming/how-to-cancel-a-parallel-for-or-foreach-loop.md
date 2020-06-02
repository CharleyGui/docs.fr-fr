---
title: 'Procédure : annuler une boucle Parallel.For ou ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288223"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="657a1-102">Procédure : annuler une boucle Parallel.For ou ForEach</span><span class="sxs-lookup"><span data-stu-id="657a1-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="657a1-103">Les méthodes <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> prennent en charge l'annulation via l'utilisation de jetons d'annulation.</span><span class="sxs-lookup"><span data-stu-id="657a1-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="657a1-104">Pour plus d'informations sur l'annulation en général, consultez [Annulation](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="657a1-104">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="657a1-105">Dans une boucle parallèle, vous fournissez <xref:System.Threading.CancellationToken> à la méthode dans le paramètre <xref:System.Threading.Tasks.ParallelOptions> et vous joignez l’appel parallèle dans un bloc try-catch.</span><span class="sxs-lookup"><span data-stu-id="657a1-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="657a1-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="657a1-106">Example</span></span>  
 <span data-ttu-id="657a1-107">L'exemple suivant montre comment annuler un appel à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="657a1-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="657a1-108">Vous pouvez appliquer la même approche à un appel <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="657a1-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="657a1-109">Si le jeton qui signale l’annulation est le même jeton que celui spécifié dans l’instance <xref:System.Threading.Tasks.ParallelOptions>, alors la boucle parallèle lève une seule exception <xref:System.OperationCanceledException> lors de l’annulation.</span><span class="sxs-lookup"><span data-stu-id="657a1-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="657a1-110">Si un autre jeton provoque l’annulation, la boucle lève une exception <xref:System.AggregateException> avec une exception <xref:System.OperationCanceledException> comme InnerException.</span><span class="sxs-lookup"><span data-stu-id="657a1-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657a1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="657a1-111">See also</span></span>

- [<span data-ttu-id="657a1-112">Parallélisme des données</span><span class="sxs-lookup"><span data-stu-id="657a1-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="657a1-113">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="657a1-113">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
