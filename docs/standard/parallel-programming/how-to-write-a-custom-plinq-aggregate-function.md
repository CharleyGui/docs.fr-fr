---
title: 'Procédure : écrire une fonction d’agrégation PLINQ personnalisée'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09e128c98b61ecc4ac673d8c9911f4bac476d521
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988436"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="9bff1-102">Procédure : écrire une fonction d’agrégation PLINQ personnalisée</span><span class="sxs-lookup"><span data-stu-id="9bff1-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="9bff1-103">Cet exemple montre comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pour appliquer une fonction d’agrégation personnalisée à une séquence source.</span><span class="sxs-lookup"><span data-stu-id="9bff1-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9bff1-104">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="9bff1-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="9bff1-105">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9bff1-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bff1-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="9bff1-106">Example</span></span>  
 <span data-ttu-id="9bff1-107">L’exemple suivant calcule l’écart type d’une séquence d’entiers.</span><span class="sxs-lookup"><span data-stu-id="9bff1-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="9bff1-108">Cet exemple utilise une surcharge de l’opérateur de requête standard d’agrégation propre à PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9bff1-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="9bff1-109">Cette surcharge accepte un <xref:System.Func%603?displayProperty=nameWithType> supplémentaire en tant que troisième paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9bff1-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="9bff1-110">Ce délégué combine les résultats de tous les threads avant d’effectuer le calcul final à partir des résultats agrégés.</span><span class="sxs-lookup"><span data-stu-id="9bff1-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="9bff1-111">Dans cet exemple, nous regroupons les sommes de tous les threads.</span><span class="sxs-lookup"><span data-stu-id="9bff1-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="9bff1-112">Notez que quand un corps d’expression lambda se compose d’une expression unique, la valeur de retour du délégué <xref:System.Func%602?displayProperty=nameWithType> correspond à la valeur de l’expression.</span><span class="sxs-lookup"><span data-stu-id="9bff1-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bff1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bff1-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="9bff1-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9bff1-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
