---
title: 'Comment : annuler une requête PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635877"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="d8b7a-102">Comment : annuler une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="d8b7a-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="d8b7a-103">Les exemples suivants montrent deux façons de modifier une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="d8b7a-104">Le premier exemple montre comment annuler une requête principalement composée de parcours de données.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="d8b7a-105">Le deuxième exemple montre comment annuler une requête contenant une fonction d’utilisateur dont les calculs sont onéreux.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="d8b7a-106">Quand l'option «Uniquement mon code» est activée, Visual Studio peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur « exception non gérée par le code utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="d8b7a-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d8b7a-107">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-107">This error is benign.</span></span> <span data-ttu-id="d8b7a-108">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d8b7a-109">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="d8b7a-110">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d8b7a-111">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d8b7a-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8b7a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8b7a-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="d8b7a-113">L’infrastructure PLINQ ne restaure pas un seul <xref:System.OperationCanceledException> dans un <xref:System.AggregateException?displayProperty=nameWithType> ; le <xref:System.OperationCanceledException> doit être géré dans un bloc catch séparé.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="d8b7a-114">Si un ou plusieurs délégués utilisateurs lèvent une OperationCanceledException(externalCT) (à l’aide d’un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externe), mais pas d’autre exception et que la requête était définie en tant que `AsParallel().WithCancellation(externalCT)`, PLINQ émettra un seul <xref:System.OperationCanceledException> (externalCT) plutôt qu’un <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d8b7a-115">Toutefois, si un délégué utilisateur lève une <xref:System.OperationCanceledException>et qu’un autre délégué lève un autre type d’exception, les deux exceptions seront restaurées dans un <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="d8b7a-116">Les recommandations générales pour l’annulation sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8b7a-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="d8b7a-117">Si vous effectuez l’annulation utilisateur-délégué, vous <xref:System.Threading.CancellationToken> devez <xref:System.OperationCanceledException>informer PLINQ de l’externe et lancer un (externalCT).</span><span class="sxs-lookup"><span data-stu-id="d8b7a-117">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="d8b7a-118">Si l’annulation se produit et aucune <xref:System.OperationCanceledException> autre <xref:System.AggregateException>exception n’est lancée, alors manipulez un plutôt que un .</span><span class="sxs-lookup"><span data-stu-id="d8b7a-118">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="d8b7a-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8b7a-119">Example</span></span>

<span data-ttu-id="d8b7a-120">L’exemple suivant montre comment gérer l’annulation lorsque vous avez une fonction de calcul onéreux dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="d8b7a-121">Lorsque vous gérez l’annulation dans le code utilisateur, vous n’avez pas à utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> dans la définition de requête.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="d8b7a-122">Cependant, nous vous avons <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>recommandé <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> d’utiliser, car n’a aucun effet sur les performances de requête et il permet à l’annulation d’être traitée par les opérateurs de requête et votre code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-122">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="d8b7a-123">Pour garantir la réactivité du système, nous vous recommandons de vérifier les annulations toutes les millisecondes ; toutefois, une période jusqu'à 10 millisecondes est considérée comme acceptable.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="d8b7a-124">Cette fréquence ne doit pas avoir d’impact négatif sur le niveau de performance de votre code.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="d8b7a-125">Lorsqu’un enumérateur est éliminé, par exemple lorsque le code sort d’une boucle de préach (pour chacun dans Visual Basic) qui s’agite sur les résultats des requêtes, la requête est annulée, mais aucune exception n’est lancée.</span><span class="sxs-lookup"><span data-stu-id="d8b7a-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8b7a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8b7a-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="d8b7a-127">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d8b7a-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="d8b7a-128">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="d8b7a-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
