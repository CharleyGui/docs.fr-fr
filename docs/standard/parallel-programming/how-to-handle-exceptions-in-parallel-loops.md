---
title: 'Procédure : gérer des exceptions dans des boucles parallèles'
description: Découvrez comment gérer les exceptions dans les boucles parallèles dans .NET. Consultez un exemple d’encapsulation de toutes les exceptions de la boucle dans un System. AggregateException.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 903db7f7318a9067c31af090490bab6dd70fa0ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734476"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="e3b01-104">Procédure : gérer des exceptions dans des boucles parallèles</span><span class="sxs-lookup"><span data-stu-id="e3b01-104">How to: Handle Exceptions in Parallel Loops</span></span>

<span data-ttu-id="e3b01-105">Les surcharges <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ne possèdent pas de mécanisme permettant de gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="e3b01-105">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="e3b01-106">À cet égard, elles ressemblent à des `for` boucles normales et `foreach` ( `For` et `For Each` dans Visual Basic); une exception non gérée entraîne l’arrêt de la boucle dès que toutes les itérations en cours se terminent.</span><span class="sxs-lookup"><span data-stu-id="e3b01-106">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="e3b01-107">Quand vous ajoutez votre propre logique de gestion des exceptions à des boucles parallèles, gérez le cas dans lequel de telles exceptions peuvent être levées simultanément sur plusieurs threads et le cas dans lequel une exception levée sur un thread provoque la levée d'une autre exception sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="e3b01-107">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="e3b01-108">Vous pouvez gérer les deux cas en encapsulant toutes les exceptions de la boucle dans un <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3b01-108">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e3b01-109">L'exemple suivant montre une méthode possible.</span><span class="sxs-lookup"><span data-stu-id="e3b01-109">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3b01-110">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e3b01-110">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e3b01-111">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="e3b01-111">This error is benign.</span></span> <span data-ttu-id="e3b01-112">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e3b01-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="e3b01-113">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="e3b01-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3b01-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3b01-114">Example</span></span>  

 <span data-ttu-id="e3b01-115">Dans cet exemple, toutes les exceptions sont interceptées, puis encapsulées dans une <xref:System.AggregateException?displayProperty=nameWithType> qui est ensuite levée.</span><span class="sxs-lookup"><span data-stu-id="e3b01-115">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="e3b01-116">L'appelant peut décider des exceptions à gérer.</span><span class="sxs-lookup"><span data-stu-id="e3b01-116">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="e3b01-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3b01-117">See also</span></span>

- [<span data-ttu-id="e3b01-118">Parallélisme des données</span><span class="sxs-lookup"><span data-stu-id="e3b01-118">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="e3b01-119">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="e3b01-119">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
