---
title: 'Comment : gérer des exceptions dans une requête PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587989"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="61adb-102">Comment : gérer des exceptions dans une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="61adb-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="61adb-103">Le premier exemple de cette rubrique montre comment gérer l’exception <xref:System.AggregateException?displayProperty=nameWithType> qui peut être levée à partir d’une requête PLINQ au cours de son exécution.</span><span class="sxs-lookup"><span data-stu-id="61adb-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="61adb-104">Le deuxième exemple montre comment placer des blocs try-catch dans des délégués, le plus près possible de l’emplacement où l’exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="61adb-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="61adb-105">Vous pouvez ainsi les intercepter dès qu’ils se produisent et éventuellement poursuivre l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="61adb-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="61adb-106">Lorsque les exceptions sont autorisées à se propager vers le thread lié, il est possible qu'une requête puisse continuer à traiter des éléments après que l'exception ait été levée.</span><span class="sxs-lookup"><span data-stu-id="61adb-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="61adb-107">Dans certains cas, quand PLINQ revient à l’exécution séquentielle et qu’une exception se produit, cette dernière peut être propagée directement, et non encapsulée dans une exception <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="61adb-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="61adb-108">En outre, les exceptions <xref:System.Threading.ThreadAbortException> sont toujours propagées directement.</span><span class="sxs-lookup"><span data-stu-id="61adb-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="61adb-109">Quand l'option «Uniquement mon code» est activée, Visual Studio peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur « exception non gérée par le code utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="61adb-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="61adb-110">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="61adb-110">This error is benign.</span></span> <span data-ttu-id="61adb-111">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="61adb-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="61adb-112">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="61adb-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="61adb-113">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="61adb-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="61adb-114">Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="61adb-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="61adb-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="61adb-115">Example</span></span>

<span data-ttu-id="61adb-116">Cet exemple montre comment placer les blocs try-catch autour du code qui exécute la requête pour intercepter toute exception <xref:System.AggregateException?displayProperty=nameWithType> levée.</span><span class="sxs-lookup"><span data-stu-id="61adb-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="61adb-117">Dans cet exemple, la requête ne peut pas continuer une fois l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="61adb-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="61adb-118">Au moment où votre code d’application intercepte l’exception, PLINQ a déjà arrêté la requête sur tous les threads.</span><span class="sxs-lookup"><span data-stu-id="61adb-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="61adb-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="61adb-119">Example</span></span>

<span data-ttu-id="61adb-120">L’exemple suivant montre comment placer un bloc try-catch dans un délégué pour pouvoir intercepter une exception et poursuivre l’exécution des requêtes.</span><span class="sxs-lookup"><span data-stu-id="61adb-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="61adb-121">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="61adb-121">Compiling the Code</span></span>

- <span data-ttu-id="61adb-122">Pour compiler et exécuter ces exemples, copiez-les dans l’exemple de données PLINQ et appelez la méthode à partir de Main.</span><span class="sxs-lookup"><span data-stu-id="61adb-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="61adb-123">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="61adb-123">Robust Programming</span></span>

<span data-ttu-id="61adb-124">N’interceptez pas d’exceptions, sauf si vous savez comment les gérer pour ne pas endommager l’état de votre programme.</span><span class="sxs-lookup"><span data-stu-id="61adb-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="61adb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61adb-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="61adb-126">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="61adb-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
