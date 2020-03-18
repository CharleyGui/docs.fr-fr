---
title: 'Comment : accélérer les petits corps de boucles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139748"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="7b361-102">Comment : accélérer les petits corps de boucles</span><span class="sxs-lookup"><span data-stu-id="7b361-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="7b361-103">Une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dont le corps est court risque de s'exécuter plus lentement que la boucle séquentielle équivalente, notamment la boucle [for](../../csharp/language-reference/keywords/for.md) en C# et la boucle [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b361-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="7b361-104">La baisse des performances est provoquée par les surcharges impliquées dans le partitionnement des données et par le coût de l'appel d'un délégué sur chaque itération de boucle.</span><span class="sxs-lookup"><span data-stu-id="7b361-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="7b361-105">Pour résoudre ces scénarios, la classe <xref:System.Collections.Concurrent.Partitioner> offre la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, ce qui vous permet de fournir une boucle séquentielle pour le corps du délégué, afin que celui-ci soit appelé une seule fois par partition, au lieu d'une fois par itération.</span><span class="sxs-lookup"><span data-stu-id="7b361-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="7b361-106">Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="7b361-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b361-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7b361-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="7b361-108">L'approche illustrée dans cet exemple est utile quand la boucle exécute une quantité minimale de travail.</span><span class="sxs-lookup"><span data-stu-id="7b361-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="7b361-109">À mesure que le travail devient de plus en plus gourmand en ressources informatiques, vous obtiendrez probablement des performances identiques ou meilleures en utilisant une boucle <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec le partitionneur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7b361-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b361-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b361-110">See also</span></span>

- [<span data-ttu-id="7b361-111">Parallélisme de données</span><span class="sxs-lookup"><span data-stu-id="7b361-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="7b361-112">Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)</span><span class="sxs-lookup"><span data-stu-id="7b361-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="7b361-113">Itérateurs (C#)</span><span class="sxs-lookup"><span data-stu-id="7b361-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="7b361-114">Itérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b361-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="7b361-115">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="7b361-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
