---
title: 'Comment : gérer des exceptions dans des boucles parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453011"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="55750-102">Comment : gérer des exceptions dans des boucles parallèles</span><span class="sxs-lookup"><span data-stu-id="55750-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="55750-103">Les surcharges <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ne possèdent pas de mécanisme permettant de gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="55750-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="55750-104">À cet égard, elles ressemblent à des `for` normales et des boucles de `foreach` (`For` et `For Each` dans Visual Basic); une exception non gérée entraîne l’arrêt de la boucle dès que toutes les itérations en cours d’exécution se terminent.</span><span class="sxs-lookup"><span data-stu-id="55750-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="55750-105">Quand vous ajoutez votre propre logique de gestion des exceptions à des boucles parallèles, gérez le cas dans lequel de telles exceptions peuvent être levées simultanément sur plusieurs threads et le cas dans lequel une exception levée sur un thread provoque la levée d'une autre exception sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="55750-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="55750-106">Vous pouvez gérer les deux cas en encapsulant toutes les exceptions de la boucle dans un <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55750-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="55750-107">L'exemple suivant montre une méthode possible.</span><span class="sxs-lookup"><span data-stu-id="55750-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55750-108">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="55750-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="55750-109">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="55750-109">This error is benign.</span></span> <span data-ttu-id="55750-110">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="55750-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="55750-111">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon code » sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="55750-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55750-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="55750-112">Example</span></span>  
 <span data-ttu-id="55750-113">Dans cet exemple, toutes les exceptions sont interceptées, puis encapsulées dans une <xref:System.AggregateException?displayProperty=nameWithType> qui est ensuite levée.</span><span class="sxs-lookup"><span data-stu-id="55750-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="55750-114">L'appelant peut décider des exceptions à gérer.</span><span class="sxs-lookup"><span data-stu-id="55750-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="55750-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55750-115">See also</span></span>

- [<span data-ttu-id="55750-116">Parallélisme de données</span><span class="sxs-lookup"><span data-stu-id="55750-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="55750-117">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="55750-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
