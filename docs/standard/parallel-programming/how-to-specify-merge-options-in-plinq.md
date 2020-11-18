---
title: 'Procédure : spécifier des options de fusion avec PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 91c5ac91538942368b66399bf0bc0132a15bf667
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825596"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="4400f-102">Procédure : spécifier des options de fusion avec PLINQ</span><span class="sxs-lookup"><span data-stu-id="4400f-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="4400f-103">Cet exemple montre comment spécifier les options de fusion qui seront appliquées à tous les opérateurs suivants dans une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="4400f-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="4400f-104">Il n’est pas nécessaire de définir explicitement les options de fusion, mais cela peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="4400f-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="4400f-105">Pour plus d’informations sur les options de fusion, consultez [Options de fusion en PLINQ](merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="4400f-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4400f-106">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="4400f-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="4400f-107">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="4400f-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4400f-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4400f-108">Example</span></span>  
 <span data-ttu-id="4400f-109">L’exemple suivant montre le comportement des options de fusion dans un scénario de base qui a une source non ordonnée et qui applique une fonction coûteuse à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="4400f-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="4400f-110">Dans les cas où l’option <xref:System.Linq.ParallelMergeOptions.AutoBuffered> entraînerait une latence indésirable avant la transmission du premier élément, essayez l’option <xref:System.Linq.ParallelMergeOptions.NotBuffered> pour transmettre des éléments de résultat plus rapidement et plus facilement.</span><span class="sxs-lookup"><span data-stu-id="4400f-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4400f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4400f-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="4400f-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4400f-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
